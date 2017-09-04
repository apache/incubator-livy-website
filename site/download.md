---
layout: page
title: Livy - Downloads
description: Livy Downloads page
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

## {{ site.data.project.name }} Downloads

{{ site.data.project.name }} is released as a source artifact, and also through Maven.

### Source releases

<table class="table table-hover sortable">
    <thead>
        <tr>
            <th><b>Name</b></th>
            <th><b>Archive</b></th>
            <th><b>MD5</b></th>
            <th><b>SHA-512</b></th>
            <th><b>signature</b></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>{{ site.data.project.name }} {{site.data.project.latest_release}} (zip)</td>
            <td><a href="http://www.apache.org/dyn/closer.lua/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-bin.zip">zip</a></td>
            <td><a href="http://www.apache.org/dist/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-bin.zip.md5">MD5</a></td>
            <td><a href="http://www.apache.org/dist/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-bin.zip.sha512">SHA-512</a></td>
            <td><a href="http://www.apache.org/dist/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-bin.zip.asc">ASC</a></td>
        </tr>
        <tr>
            <td>{{ site.data.project.name }} {{site.data.project.latest_release}} (source zip)</td>
            <td><a href="http://www.apache.org/dyn/closer.lua/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-src.zip">zip</a></td>
            <td><a href="http://www.apache.org/dist/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-src.zip.md5">MD5</a></td>
            <td><a href="http://www.apache.org/dist/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-src.zip.sha512">SHA-512</a></td>
            <td><a href="http://www.apache.org/dist/incubator/{{site.data.project.unix_name}}/{{site.data.project.latest_release}}/{{site.data.project.unix_name}}-{{site.data.project.latest_release}}-src.zip.asc">ASC</a></td>
        </tr>
    </tbody>
</table>

You can also retrieve the source files from our [git repository](https://github.com/apache/{{ site.data.project.incubator_name }}) by typing:

<pre>
git clone {{site.data.project.source_repository_mirror}}
cd {{site.data.project.github_project_name}}
git checkout -b tags/v{{site.data.project.latest_release}} v{{site.data.project.latest_release}}
</pre>

### Release Notes

Release notes for the current and previous releases can be found in the [release history]({{ site.baseurl }}/history)

### Previous Releases

All previous releases of {{ site.data.project.name }} can be found in the [archives](http://archive.apache.org/dist/incubator/{{site.data.project.unix_name}}/).

## Verifying a Release

Instructions for checking hashes and signatures is indicated on the [Verifying Apache Software Foundation Releases](http://www.apache.org/info/verification.html) page.

Choose a source distribution in either *tar* or *zip* format,
and [verify](http://www.apache.org/dyn/closer.cgi#verify)
using the corresponding *pgp* signature (using the committer file in
[KEYS](http://www.apache.org/dist/incubator/{{ site.data.project.unix_name }}/KEYS)).
If you cannot do that, the *md5* hash file may be used to check that the
download has completed OK.

For fast downloads, current source distributions are hosted on mirror servers;
older source distributions are in the
[archive](http://archive.apache.org/dist/incubator/{{ site.data.project.unix_name }}/).
If a download from a mirror fails, retry, and the second download will likely
succeed.

For security, hash and signature files are always hosted at
[Apache](https://www.apache.org/dist/incubator/{{ site.data.project.unix_name }}/).

