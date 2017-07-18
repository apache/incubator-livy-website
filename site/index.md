---
layout: page
title: Apache Livy
tagline: Apache Livy
---
<!--
{% comment %}
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to you under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
{% endcomment %}
-->

{% include JB/setup %}

#### *Submit Jobs from Anywhere*
> Livy enables programmatic, fault-tolerant, multi-tenant submission of Spark jobs from web/mobile apps (no Spark
client needed). So, multiple users can interact with your Spark cluster concurrently and reliably.

#### *Use Interactive Scala or Python*
> Livy speaks either Scala or Python, so clients can communicate with your Spark cluster via either language remotely.
Also, batch job submissions can be done in Scala, Java, or Python.

#### *No Code Changes Needed*
> Don't worry, no changes to existing programs are needed to use Livy. Just build Livy with Maven, deploy the
configuration file to your Spark cluster, and you're off! Check out [Get Started]({{ site.baseurl }}/get-started) to
get going.

### What is Apache Livy?

Apache Livy is a service that enables easy interaction with a Spark cluster over a REST interface. It enables easy
submission of Spark jobs or snippets of Spark code, synchronous or asynchronous result retrieval, as well as Spark
Context management, all via a simple REST interface or a RPC client library. Apache Livy also simplifies the
interaction between Spark from application servers, thus enabling the use of Spark for interactive web/mobile
applications. Additional features include:

* Have long running Spark Contexts that can be used for multiple Spark jobs, by multiple clients
* Share cached RDDs or Dataframes across multiple jobs and clients
* Multiple Spark Contexts can be managed simultaneously, and the Spark Contexts run on the cluster (YARN/Mesos) instead
of the Livy Server, for good fault tolerance and concurrency
* Jobs can be submitted as precompiled jars, snippets of code or via java/scala client API
* Ensure security via secure authenticated communication

To learn more, [watch this tech session video](https://youtu.be/C_3iEf_KNv8) from Spark Summit West 2016.

<img src="/assets/images/livy-architecture.png" alt="Architecture" style="width: 90%; display: block; margin: 0 auto;"/>
