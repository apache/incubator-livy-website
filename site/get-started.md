---
layout: page
title: Livy - Getting Started
tagline: Getting Started
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

## Getting Started

### 1. Install Livy
Download Livy packages from [here]({{ site.baseurl }}/download).

### 2. Run Livy
To run the Livy server, you will also need an Apache Spark installation. You can get Spark releases at
<https://spark.apache.org/downloads.html>. Livy requires at least Spark 1.6 and supports both Scala 2.10 and 2.11
builds of Spark. To run Livy with local sessions, first export these variables:

`export SPARK_HOME=/usr/lib/spark`

`export HADOOP_CONF_DIR=/etc/hadoop/conf`

Then start the server with:

`./bin/livy-server`

Livy uses the Spark configuration under `SPARK_HOME` by default. You can override the Spark configuration by setting the
`SPARK_CONF_DIR` environment variable before starting Livy.

It is strongly recommended to configure Spark to submit applications in YARN cluster mode. That makes sure that user
sessions have their resources properly accounted for in the YARN cluster, and that the host running the Livy server
doesn't become overloaded when multiple user sessions are running.

### 3. Configure Livy
Livy uses a few configuration files under configuration the directory, which by default is the conf directory under the
Livy installation. An alternative configuration directory can be provided by setting the `LIVY_CONF_DIR` environment
variable when starting Livy.

The configuration files used by Livy are:

* **livy.conf:** contains the server configuration. The Livy distribution ships with a default configuration file
template listing available configuration keys and their default values.
* **spark-blacklist.conf:** list Spark configuration options that users are not allowed to override. These options will
be restricted to either their default values, or the values set in the Spark configuration used by Livy.
* **log4j.properties:** configuration for Livy logging. Defines log levels and where log messages will be written to.
The default configuration template will print log messages to stderr.

### 4. Start using Livy

Once the Livy server is running, you can connect to it, by default, on port 8998 (this can be changed with the 
`livy.server.port` config option). Some examples to get started are provided [here]({{ site.baseurl }}/examples), 
or you can check out the API documentation:

* [REST API]({{ site.baseurl }}/docs/latest/rest-api.html)
* [Programmatic API]({{ site.baseurl }}/docs/latest/programmatic-api.html)
