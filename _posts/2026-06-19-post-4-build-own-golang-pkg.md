---
title:  "Build Own Common Go Package"
date: 2026-06-19
permalink: /posts/post-4
tags:
  - golang
  - cicd
---
---

# Build Your Own Common Go Package (common-go)

This guide walks you through creating a reusable Go package called `common-go` with log, cache, and database utilities that can be imported in other projects.

---

## Step 1: Create GitHub Repository

1. Create a new repository on GitHub named `common-go`
2. Clone it to your local machine:

```bash
git clone https://github.com/YOUR-USERNAME/common-go.git
cd common-go
```

---

## Step 2: Initialize Go Module

Create the module definition for your package:

```bash
go mod init github.com/YOUR-USERNAME/common-go
```

This creates a `go.mod` file:

```
module github.com/YOUR-USERNAME/common-go

go 1.21
```

---

## Step 3: Project Structure

Organize your package with subpackages for each concern:

```
common-go/
├── go.mod
├── go.sum
├── README.md
├── .gitignore
├── log/
│   ├── logger.go
│   ├── level.go
│   └── formatter.go
├── cache/
│   ├── cache.go
│   ├── memory.go
│   └── redis.go
├── database/
│   ├── db.go
│   ├── postgres.go
│   ├── mysql.go
│   └── migration.go
└── examples/
    ├── log_example.go
    ├── cache_example.go
    └── database_example.go
```

---

## Step 4: Add Dependencies to go.mod

Your `go.mod` should include necessary dependencies:

```bash
go get github.com/lib/pq          # PostgreSQL driver
go get github.com/go-sql-driver/mysql  # MySQL driver
```

This updates your `go.mod` and `go.sum` files automatically.

---

## Step 5: Push to GitHub

```bash
git add .
git commit -m "Initial commit: Add log, cache, and database packages"
git push origin main
```

---

## Step 6: Use in Your Projects

In any Go project, add to your `go.mod`:

```bash
go get github.com/YOUR-USERNAME/common-go@v1.0.0
```

Or add directly to `go.mod`:

```
require github.com/YOUR-USERNAME/common-go v1.0.0
```

---

## Version Management & Releases

### Create a Release Tag

```bash
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0
```

### Update Version in Projects

```bash
# Update to latest
go get -u github.com/YOUR-USERNAME/common-go

# Update to specific version
go get github.com/YOUR-USERNAME/common-go@v1.0.1
```

---

## Step 7: Setup CI/CD with GitHub Actions

GitHub Actions automatically tests your code and manages releases. When you push a tag, it becomes available for import in other projects.

### 7a: Create Test Workflow

Create file: `.github/workflows/test.yml`

```yaml
name: Tests

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        go-version: ['1.20', '1.21', '1.22']

    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Go
      uses: actions/setup-go@v4
      with:
        go-version: ${{ matrix.go-version }}
    
    - name: Cache Go modules
      uses: actions/cache@v3
      with:
        path: ~/go/pkg/mod
        key: ${{ runner.os }}-go-${{ hashFiles('**/go.sum') }}
        restore-keys: |
          ${{ runner.os }}-go-
    
    - name: Download dependencies
      run: go mod download
    
    - name: Run tests
      run: go test -v -race -coverprofile=coverage.out ./...
    
    - name: Upload coverage to Codecov
      uses: codecov/codecov-action@v3
      with:
        file: ./coverage.out
    
    - name: Run linter
      uses: golangci/golangci-lint-action@v3
      with:
        version: latest
```

### 7b: Create Release Workflow

Create file: `.github/workflows/release.yml`

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

jobs:
  release:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - name: Set up Go
      uses: actions/setup-go@v4
      with:
        go-version: '1.21'

    - name: Run tests
      run: go test -v -race ./...

    - name: Create Release
      uses: actions/create-release@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tag_name: ${{ github.ref }}
        release_name: Release ${{ github.ref }}
        body: |
          ## Changes
          - [Check commits](https://github.com/${{ github.repository }}/compare/${{ github.ref }}~1...${{ github.ref }})
          
          ## Installation
          ```bash
          go get github.com/${{ github.repository }}@${{ github.ref }}
          ```
        draft: false
        prerelease: false
```

### 7c: Add Tests to Your Package

Create test files for each package

---

## Step 8: Automate Release Process

### 8a: Create Local Release Script

Create file: `scripts/release.sh`

```bash
#!/bin/bash

# Usage: ./scripts/release.sh v1.0.0

VERSION=$1

if [ -z "$VERSION" ]; then
    echo "Usage: ./scripts/release.sh <version>"
    echo "Example: ./scripts/release.sh v1.0.0"
    exit 1
fi

# Check if version is valid semantic version
if ! [[ $VERSION =~ ^v[0-9]+\.[0-9]+\.[0-9]+$ ]]; then
    echo "Invalid version format. Use v1.0.0 format"
    exit 1
fi

echo "Creating release for $VERSION..."

# Run tests before releasing
echo "Running tests..."
go test -v ./... || exit 1

# Create tag
echo "Creating git tag..."
git tag -a "$VERSION" -m "Release $VERSION"

# Push tag to GitHub
echo "Pushing to GitHub..."
git push origin "$VERSION"

echo "✅ Release $VERSION created successfully!"
echo "📦 Package will be available at: github.com/YOUR-USERNAME/common-go@$VERSION"
```

Make it executable:

```bash
chmod +x scripts/release.sh
```

### 8b: Use Release Script

```bash
./scripts/release.sh v1.0.0
./scripts/release.sh v1.0.1
./scripts/release.sh v1.1.0
```

---

## Step 9: How It Works - Auto Import Flow

```
┌─────────────────────────────────────────────────────────────────┐
│ 1. You push code + tag (git push origin v1.0.0)                 │
│    └─> Triggers GitHub Actions                                  │
├─────────────────────────────────────────────────────────────────┤
│ 2. GitHub Actions runs:                                         │
│    ├─> Tests (test.yml)                                         │
│    ├─> Linting                                                   │
│    └─> Creates Release (release.yml)                            │
├─────────────────────────────────────────────────────────────────┤
│ 3. Go Module Proxy (proxy.golang.org) auto-caches               │
│    └─> Usually takes 1-2 minutes                                │
├─────────────────────────────────────────────────────────────────┤
│ 4. Available for import in other projects:                      │
│    └─> go get github.com/YOUR-USERNAME/common-go@v1.0.0        │
└─────────────────────────────────────────────────────────────────┘
```

---

## Step 9: Full CI/CD Workflow

### 9a: Typical Development Flow

```bash
# 1. Make changes locally
vim log/logger.go

# 2. Run tests locally
go test -v ./...

# 3. Commit changes
git add .
git commit -m "feat: add debug logging option"
git push origin feature-branch

# 4. Create Pull Request on GitHub
# (GitHub Actions automatically tests the PR)

# 5. Merge to main branch

# 6. Create release tag
git tag -a v1.0.1 -m "Fix: improve log performance"
git push origin v1.0.1

# 7. GitHub Actions automatically:
#    - Runs all tests
#    - Creates Release on GitHub
#    - Go proxy caches the package

# 8. Other projects can now use it:
go get github.com/YOUR-USERNAME/common-go@v1.0.1
```

### 9b: View Release Status

1. Go to: `https://github.com/YOUR-USERNAME/common-go/releases`
2. See all releases with version history
3. View auto-generated release notes

### 9c: Monitor Package Usage

Check if package is indexed:
```bash
# Wait ~2 minutes after tag push, then:
go get github.com/YOUR-USERNAME/common-go@latest

# Or query Go module proxy directly:
curl https://proxy.golang.org/github.com/YOUR-USERNAME/common-go/@latest
```

---

## Step 10: Optional - Private Modules (for private packages)

If you want a private package (not public GitHub), setup:

Create file: `.github/workflows/publish-private.yml`

```yaml
name: Publish to Private Registry

on:
  push:
    tags:
      - 'v*'

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Go
      uses: actions/setup-go@v4
      with:
        go-version: '1.21'
    
    - name: Configure Git credentials
      run: |
        git config --global url."https://${{ secrets.GITHUB_TOKEN }}@github.com/".insteadOf "https://github.com/"
    
    - name: Publish module
      run: |
        go mod tidy
        echo "✅ Module published"
```

---

## Quick Reference - CI/CD Commands

| Task | Command |
|------|---------|
| Create release | `git tag -a v1.0.0 -m "msg" && git push origin v1.0.0` |
| Run tests locally | `go test -v ./...` |
| Check coverage | `go test -cover ./...` |
| Run linter | `golangci-lint run` |
| View releases | `https://github.com/YOUR-USERNAME/common-go/releases` |
| Check proxy | `curl https://proxy.golang.org/github.com/YOUR-USERNAME/common-go/@latest` |

---

## Troubleshooting CI/CD

**Issue: Tests fail in CI but pass locally**
- Ensure Go versions match
- Check all dependencies are in go.mod
- Run in same environment: `docker run -it golang:1.21 bash`

**Issue: Release not available after tag push**
- Wait 2-5 minutes for Go proxy to cache
- Verify tag format: `v1.0.0` (must include `v`)
- Check: `git tag -l` and `git show v1.0.0`

**Issue: Module not found with `go get`**
- Ensure repo is public
- Verify module name in go.mod
- Check GitHub Actions ran successfully

**Issue: GitHub Actions permission errors**
- Verify `GITHUB_TOKEN` is available (default in GitHub Actions)
- Check workflow has write permissions

---

