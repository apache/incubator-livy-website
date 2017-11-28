---
layout: page
title: Livy - Community
description: Livy Community Page
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

## {{ site.data.project.name }} Community

Every volunteer project obtains its strength from the people involved in it. We invite you to participate as much or as little as you choose.

You can:

* Use our project and provide feedback.
* Provide us with use cases.
* Report bugs and submit patches.
* Contribute code, javadocs, documentation.

### Mailing list

Get help using {{ site.data.project.short_name }} or contribute to the project on our mailing lists:

* [{{ site.data.project.user_list }}](mailto:{{ site.data.project.user_list }}) is for usage questions, help, and announcements. [subscribe](mailto:{{ site.data.project.user_list_subscribe }}?subject=send this email to subscribe),     [unsubscribe](mailto:{{ site.data.project.dev_list_unsubscribe }}?subject=send this email to unsubscribe), [archives]({{ site.data.project.user_list_archive_mailarchive }})
* [{{ site.data.project.dev_list }}](mailto:{{ site.data.project.dev_list }}) is for people who want to contribute code to {{ site.data.project.short_name }}. [subscribe](mailto:{{ site.data.project.dev_list_subscribe }}?subject=send this email to subscribe), [unsubscribe](mailto:{{ site.data.project.dev_list_unsubscribe }}?subject=send this email to unsubscribe), [archives]({{ site.data.project.dev_list_archive_mailarchive }})
* [{{ site.data.project.commits_list }}](mailto:{{ site.data.project.commits_list }}) is for commit messages and patches to {{ site.data.project.short_name }}. [subscribe](mailto:{{ site.data.project.commits_list_subscribe }}?subject=send this email to subscribe), [unsubscribe](mailto:{{ site.data.project.commits_list_unsubscribe }}?subject=send this email to unsubscribe), [archives]({{ site.data.project.commits_list_archive_mailarchive }})
* [{{ site.data.project.issues_list }}](mailto:{{ site.data.project.issues_list }}) is for changes and comments to {{ site.data.project.short_name }} issues. [subscribe](mailto:{{ site.data.project.issues_list_subscribe }}?subject=send this email to subscribe), [unsubscribe](mailto:{{ site.data.project.issues_list_unsubscribe }}?subject=send this email to unsubscribe), [archives]({{ site.data.project.issues_list_archive_mailarchive }})


### Issue tracking

#### Bug Reports

Found bug? Enter an issue in the [Issue Tracker](https://issues.apache.org/jira/browse/{{ site.data.project.jira }}).

Before submitting an issue, please:

* Verify that the bug does in fact exist.
* Search the issue tracker to verify there is no existing issue reporting the bug you've found.
* Consider tracking down the bug yourself in the Livy source code and submitting a patch along with your bug report. This is a great time saver for the Livy developers and helps ensure the bug will be fixed quickly.


#### Feature Requests

Enhancement requests for new features are also welcome. The more concrete and rational the request is, the greater the chance it will be incorporated into future releases.


  [https://issues.apache.org/jira/browse/{{ site.data.project.jira }}](https://issues.apache.org/jira/browse/{{ site.data.project.jira }})

### Contributing

#### Finding an Issue

Once you find an issue that you would like to work on, if no one is working on it, assign it to yourself (only if you
intend to work on it shortly though). Except for the very smallest items, it’s a very good idea to discuss your intended
approach either on the issue's JIRA or on the dev mailing list. You are more likely to have your patch reviewed and
committed if you’ve already got buy-in from the livy community before you start.

#### Submitting a Fix

As you are writing your patch, please keep the following things in mind:

1. Include tests with your patch. If your patch does not include tests, it will not be accepted. If you are
unsure how to write tests for a particular component, please ask on the dev mailing list for guidance.

2. Keep your patch narrowly targeted to the problem described by the JIRA. It is important that we maintain
discipline about the scope of each patch. In general, if you find a bug while working on a specific feature, file a JIRA
for the bug, check if you can assign it to yourself and fix it independently of the feature. This helps us to
differentiate between bug fixes and features and allows us to build stable maintenance releases.

3. Write a clear commit message, with a short, descriptive title and a message that is exactly long
enough to explain what the problem was and how it was fixed. 
  * The PR title should be of the form [LIVY-xxxx] Title, where LIVY-xxxx is the relevant JIRA number and Title may be
  the JIRA's title or a more specific title describing the PR itself.
  * If the pull request is still a work in progress, and so is not ready to be merged, but needs to be pushed to Github
  to facilitate review, then add [WIP] after the component.

4. Link your patch with it's associated JIRA by adding a link on the JIRA to your pull request and including a link to
the JIRA in your pull request.

### Source Code

The project sources are accessible via the [source code repository]({{ site.data.project.source_repository }}) which is also mirrored in [GitHub]({{ site.data.project.source_repository_mirror }})


### Website Source Code

The project website sources are accessible via the [website source code repository]({{ site.data.project.website_repository }}) which is also mirrored in [GitHub]({{ site.data.project.website_repository_mirror }})
