---
layout: page
title: Livy - History
description: Release History
group: nav-right
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

## {{ site.data.project.name }} Releases

For a full list of releases, see
<a href="https://github.com/apache/{{ site.data.project.incubator_name }}/releases">GitHub</a>.
Downloads are available on the
[downloads page]({{ site.baseurl }}/download).

## <a href="https://github.com/apache/{{ site.data.project.incubator_name }}/releases/tag/v0.5.0-incubating">0.6.0-incubating</a> / 2019-04-01
{: #v0-6-0-incubating}

New features

* Livy 0.6.0 now requires Java 8, Scala 2.11 and Spark >= 2.2.0.

* Added support for all current versions of Spark (2.2.x to 2.4.x).

* [<a href="https://issues.apache.org/jira/browse/LIVY-489">LIVY-489</a>]
  New, experimental Hive-compatible JDBC / ODBC server.

* [<a href="https://issues.apache.org/jira/browse/LIVY-551">LIVY-551</a>]
  Impersonation support for all REST endpoints, for better integration with proxy servers.

* [<a href="https://issues.apache.org/jira/browse/LIVY-41">LIVY-41</a>]
  Session naming support.


## <a href="https://github.com/apache/{{ site.data.project.incubator_name }}/releases/tag/v0.5.0-incubating">0.5.0-incubating</a> / 2018-02-05
{: #v0-5-0-incubating}

New features

* [<a href="https://issues.apache.org/jira/browse/LIVY-7">LIVY-7</a>]
  Added autocompletion to REST API and Scala API for Interactive Sessions

* [<a href="https://issues.apache.org/jira/browse/LIVY-19">LIVY-19</a>]
  Added Spark SQL interpreter for Interactive Sessions

* [<a href="https://issues.apache.org/jira/browse/LIVY-104">LIVY-104</a>]
  Updated Livy project to build using Scala 2.11

* [<a href="https://issues.apache.org/jira/browse/LIVY-245">LIVY-245</a>]
  Added support for shared variables across Jobs

* [<a href="https://issues.apache.org/jira/browse/LIVY-299">LIVY-299</a>]
  Support multi-line output in statements

* [<a href="https://issues.apache.org/jira/browse/LIVY-397">LIVY-397</a>]
  Support multiple languages in a single Session

## <a href="https://github.com/apache/{{ site.data.project.incubator_name }}/releases/tag/v0.4.0-incubating">0.4.0-incubating</a> / 2017-09-01
{: #v0-4-0-incubating}

Our first Apache release!

New features

* [<a href="https://issues.apache.org/jira/browse/LIVY-87">LIVY-87</a>]
  Create a Livy Web UI to monitor sessions
* [<a href="https://issues.apache.org/jira/browse/LIVY-348">LIVY-348</a>]
  Improve Livy's ACLs
