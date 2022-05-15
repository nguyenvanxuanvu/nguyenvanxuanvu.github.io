+++
title = "System serve blogs to massive readers (10k tps)"
description = ""
tags = [
    "development",
]
date = "2022-05-11"
categories = [
    "Development",
    "system",
]
+++

## 1. Introduction

First of all, a blog (a shortened version of “weblog”) is an online journal or informational website displaying information in reverse chronological order, with the latest posts appearing first, at the top. It is a platform where a writer or a group of writers share their views on an individual subject.

Today, there are more than 570 million blogs on the web.

**And what is the purpose of a blog?**

The main purpose of a blog is to connect you to the relevant audience. Another one is to boost your traffic and send quality leads to your website.

So to grow in the long term and connect with more people, you need a system that can handle a large and effective traffic for your blog/homepage. 

And in this blog, specific to the problem here is **10000 transactions per second (10k tps)**. 

To do that, let's work together to find solutions for your own system.

## 2. Point out the problems

After researching and asking some more experienced people, I think to build the system as mentioned above, we will encounter 2 main types of problems:
- **About product (blog):**
  - Your blog is for the purpose of reading articles only ?
  - In addition to serving articles, you are also welcome to allow your readers to send you messages or do other things such as donate ?
- **About technology:**
  - what technologies help your system achieve 10k tps ?

In this post, I choose to build a system for reading blogs. Other post data-oriented features such as sending messages or donations will be expanded in the future. 

As for the technology used and the specifics of the system, let's go to the next sections of the blog


## 3. Main architecture for my system


![](/posts/basic.png)

With a simple system that can only read blogs with a small number of users, the above basic components are enough to operate the system.
The client sends a request to the web server and the web server retrieves data from the database and returns the information to the client.

Sounds simple right?

**But for technology, it's never enough.**

In order to meet a larger amount of data access and a larger number of users, and improve performance, the above system faces many problems that need to be solved.

## 4. Some solutions for mystem to gain the purpose 10k tps
With the design of the above sections, you can basically build a system for your blog. However, some of the following problems will occur when you have a large amount of traffic, specifically here is 10k tps. Here are the 2 main issues:
- **Problem from client to web server layer:**
  - When we use the server to run the website or run the software, but when the server has a problem, we can't access it anymore, all the work is delayed, to switch to a backup server, we have to It takes a lot of time, delays a lot of work.

  - When many connections to a server cause that server to be overloaded but the backup server is not running at all, so we will not use up all the performance and the access speed will be reduced.

  - The system will reduce security because users can directly access the server.

  -> To solve this problem, we come to a kind of technology and its effect: **load balancer**

  Let talk about **load balancer**

  Load balancers distribute incoming client requests to computing resources such as application servers and databases. In each case, the load balancer returns the response from the computing resource to the appropriate client. Load balancers are effective at:
  - Preventing requests from going to unhealthy servers
  - Preventing overloading resources
  - Helping to eliminate a single point of failure
  
  ![](/posts/load-balancing.png)

  Load balancers can be implemented with hardware (expensive) or with software such as HAProxy.
- **Problem from web server to database layer:**
  - Let's look at the problem again, we are building a 10k tps system, so fast data retrieval is indispensable.
  - For every data access, the server has to call the database to find the appropriate data. Of course this is acceptable for a system with a small number of users, but given the problem, it reduces performance significantly and will not be able to handle a large amount of traffic.
  
  -> To solve this problem, we come to a kind of technology and its effect: **catching**

  Let talk about **catching**

  Caching improves page load times and can reduce the load on your servers and databases. In this model, the dispatcher will first lookup if the request has been made before and try to find the previous result to return, in order to save the actual execution.

  Databases often benefit from a uniform distribution of reads and writes across its partitions. Popular items can skew the distribution, causing bottlenecks. Putting a cache in front of a database can help absorb uneven loads and spikes in traffic.

  ![](/posts/cache.jpg)

  In this diagram, You will see the steps the system looks for when using the cache. First of all, the dispatcher will search for data in the cache first, when it is not in the cache, it will search the database and save it in the cache.

  This way, when the data already exists in the cache, the system's data retrieval time will be significantly reduced.



## 5. Complete system

## 6. Further issues for this system


