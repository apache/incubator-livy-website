---
layout: page
title: Livy - Release Process
tagline: Release Process
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

# Preparing Livy Releases

*Note: This document is a work in progress and is not guaranteed to be a comprehensive release guide*

## Overview

The release manger for a Apache Livy release is in charge of:

1. Cut and update branches and tags
1. Create and publish release distros and artifacts to staging locations
1. Call a vote to authorize release
1. Publish the release (once a vote passes)
1. After the release is complete

### Prepare for release

If this is your first release it may be useful to read some of the following:

- <a href="http://www.apache.org/dev/#releases">Apache Software Release Documentation</a>
- <a href="http://incubator.apache.org/policy/incubation.html#releases">Apache Incubator Podling Release Policies</a>
- <a href="https://www.apache.org/dev/release-signing.html">Apache Guide on Signing Releases</a>
- <a href="https://spark.apache.org/release-process.html">The Apache Spark Release Guide</a> (for comparison)

### Cut and update branches and tags

1. Create new branch (from master if a major/minor version, or branch-X.x for a maintenance version for version X.x) then push it to apache.
1. Update the master branch with to the next version if this is a major/minor release.
(<a href="https://github.com/apache/incubator-livy/commit/99c385d6436120e3767393ba76dcaa982d7b9929">Example commit</a>)
1. Remove SNAPSHOT from the version on branch then cut rc1 tag.
(<a href="https://github.com/apache/incubator-livy/commit/b88223a6416ca5419257c92e81c394269a008729">Example commit</a>)
1. After cutting the rc1 tag you can then update the branch with the next maintenance version. (Note: If you do this prior to release any changes between rc’s will be individually cherry-picked)
(<a href="https://github.com/apache/incubator-livy/commit/dd9a78245e5f67b2c9a6cd62f7bbda2175ac0bc9">Example commit</a>)

### Create and publish release distros and artifacts to staging locations

1. Make sure your public key is in the KEY file in the Livy Dist. Directions for creating your key for releases can be found
<a href="https://www.apache.org/dev/release-signing.html">here</a>.
1. Publish the release archives to the Apache dev dist for dev testing (these will be moved to the release dist after a successful vote).
    1. Set env variables as described in ``dev/release-build.sh`` (or utilize the script's prompts).
    1. Run ``dev/release-build.sh package`` (Note: You may need to run ``GPG_TTY=$(tty); export GPG_TTY`` for the script to work).
    1. Double check the distros has been uploaded to the <a href="https://dist.apache.org/repos/dist/dev/incubator/livy">dev dist</a>.
1. Use ``dev/release-build.sh publish-release`` to push the release artifacts to the apache staging repo
(Note: Make sure sha1 is installed before running the script). Double check that the artifacts were published successfully by checking the
<a href="https://repository.apache.org/#stagingRepositories">staging repo</a>.

### Call a vote to authorize release

1. Email the Livy dev mailing list to call for vote on the release candidate and make sure to note that if it passes it will go to an official vote on the Incubator general mailing list.
(<a href="https://www.mail-archive.com/dev@livy.incubator.apache.org/msg00294.html">Example email</a>)
1. If the vote passes email the Incubator general list to call for a PMC vote. 
(<a href="https://www.mail-archive.com/general@incubator.apache.org/msg62366.html">Example email</a>).
If the vote fails, address the issues raised and cut a new rc with the required fixes.

### Publish the release (once a vote passes)

1. Go to the <a href="https://repository.apache.org/#stagingRepositories">staging repo</a>, select the livy repo from the ``publish-release`` step above 
and click the "release" button at the top of the page to release the new Livy version artifacts.
1. Move the contents of the <a href="https://dist.apache.org/repos/dist/dev/incubator/livy">dev dist</a> to the 
<a href="https://dist.apache.org/repos/dist/release/incubator/livy">release dist</a> (removing the rc# from the folder name).
    1. Example steps
        ```bash
       $ svn co https://dist.apache.org/repos/dist/dev/incubator/livy/
       $ export SVN_EDITOR=vim
       $ svn mv https://dist.apache.org/repos/dist/dev/incubator/livy/0.5.0-incubating-rc2/ https://dist.apache.org/repos/dist/release/incubator/livy/0.5.0-incubating/
        ```
    1. If you updated the KEYS file during this release make sure you also copy that as well. 
1. Checkout the rc git tag and recommit it without the rc# (Example below)
    ```bash
   $ git tag -a v0.5.0-incubating -m "Apache Livy 0.5.0-incubating"
   $ git push --delete apache v0.5.0-incubating-rc1
    ```
1. Announce the release to the Incubator general, Livy dev, and Livy user mailing lists 
(<a href="Incubator general, Livy dev and Livy user">Example Email</a>), if you want you can complete the website update step below to include links in the email.

### After the release is complete
1. Open a PR to update the website with the new latest version number, release notes, and a copy of the Docs built using the new release.
1. If there were any non-blocking issues raised during the vote make sure there are open JIRAs to address them in the next release.
