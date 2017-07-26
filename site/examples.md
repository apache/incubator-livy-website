---
layout: page
title: Livy - Examples
tagline: Examples
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

# Apache Livy Examples

## Spark Example

Here's a step-by-step example of interacting with Livy in Python with the
[Requests](http://docs.python-requests.org/en/latest/) library. By default Livy runs on port 8998 (which can be changed
with the ``livy.server.port`` config option). We’ll start off with a Spark session that takes Scala code:

```shell
sudo pip install requests
```

```python
import json, pprint, requests, textwrap
host = 'http://localhost:8998'
data = {'kind': 'spark'}
headers = {'Content-Type': 'application/json'}
r = requests.post(host + '/sessions', data=json.dumps(data), headers=headers)
r.json()

{u'state': u'starting', u'id': 0, u'kind': u'spark'}
```

Once the session has completed starting up, it transitions to the idle state:

```python
session_url = host + r.headers['location']
r = requests.get(session_url, headers=headers)
r.json()

{u'state': u'idle', u'id': 0, u'kind': u'spark'}
```

Now we can execute Scala by passing in a simple JSON command:

```python
statements_url = session_url + '/statements'
data = {'code': '1 + 1'}
r = requests.post(statements_url, data=json.dumps(data), headers=headers)
r.json()

{u'output': None, u'state': u'running', u'id': 0}
```

If a statement takes longer than a few milliseconds to execute, Livy returns
early and provides a statement URL that can be polled until it is complete:

```python
statement_url = host + r.headers['location']
r = requests.get(statement_url, headers=headers)
pprint.pprint(r.json())

{u'id': 0,
  u'output': {u'data': {u'text/plain': u'res0: Int = 2'},
              u'execution_count': 0,
              u'status': u'ok'},
  u'state': u'available'}
```

That was a pretty simple example. More interesting is using Spark to estimate
Pi. This is from the [Spark Examples](https://spark.apache.org/examples.html):

```python
data = {
  'code': textwrap.dedent("""
    val NUM_SAMPLES = 100000;
    val count = sc.parallelize(1 to NUM_SAMPLES).map { i =>
      val x = Math.random();
      val y = Math.random();
      if (x*x + y*y < 1) 1 else 0
    }.reduce(_ + _);
    println(\"Pi is roughly \" + 4.0 * count / NUM_SAMPLES)
    """)
}

r = requests.post(statements_url, data=json.dumps(data), headers=headers)
pprint.pprint(r.json())

statement_url = host + r.headers['location']
r = requests.get(statement_url, headers=headers)
pprint.pprint(r.json())

{u'id': 1,
 u'output': {u'data': {u'text/plain': u'Pi is roughly 3.14004\nNUM_SAMPLES: Int = 100000\ncount: Int = 78501'},
             u'execution_count': 1,
             u'status': u'ok'},
 u'state': u'available'}
```

Finally, close the session:

```python
session_url = 'http://localhost:8998/sessions/0'
requests.delete(session_url, headers=headers)

<Response [204]>
```

### PySpark Example

PySpark has the same API, just with a different initial request:

```python
data = {'kind': 'pyspark'}
r = requests.post(host + '/sessions', data=json.dumps(data), headers=headers)
r.json()

{u'id': 1, u'state': u'idle'}
```

The Pi example from before then can be run as:

```python
data = {
  'code': textwrap.dedent("""
    import random
    NUM_SAMPLES = 100000
    def sample(p):
      x, y = random.random(), random.random()
      return 1 if x*x + y*y < 1 else 0

    count = sc.parallelize(xrange(0, NUM_SAMPLES)).map(sample).reduce(lambda a, b: a + b)
    print "Pi is roughly %f" % (4.0 * count / NUM_SAMPLES)
    """)
}

r = requests.post(statements_url, data=json.dumps(data), headers=headers)
pprint.pprint(r.json())

{u'id': 12,
u'output': {u'data': {u'text/plain': u'Pi is roughly 3.136000'},
            u'execution_count': 12,
            u'status': u'ok'},
u'state': u'running'}
```

### SparkR Example

SparkR has the same API:

```python
data = {'kind': 'sparkr'}
r = requests.post(host + '/sessions', data=json.dumps(data), headers=headers)
r.json()

{u'id': 1, u'state': u'idle'}
```

The Pi example from before then can be run as:

```python
data = {
  'code': textwrap.dedent("""
    n <- 100000
    piFunc <- function(elem) {
      rands <- runif(n = 2, min = -1, max = 1)
      val <- ifelse((rands[1]^2 + rands[2]^2) < 1, 1.0, 0.0)
      val
    }
    piFuncVec <- function(elems) {
      message(length(elems))
      rands1 <- runif(n = length(elems), min = -1, max = 1)
      rands2 <- runif(n = length(elems), min = -1, max = 1)
      val <- ifelse((rands1^2 + rands2^2) < 1, 1.0, 0.0)
      sum(val)
    }
    rdd <- parallelize(sc, 1:n, slices)
    count <- reduce(lapplyPartition(rdd, piFuncVec), sum)
    cat("Pi is roughly", 4.0 * count / n, "\n")
    """)
}

r = requests.post(statements_url, data=json.dumps(data), headers=headers)
pprint.pprint(r.json())

{u'id': 12,
 u'output': {u'data': {u'text/plain': u'Pi is roughly 3.136000'},
             u'execution_count': 12,
             u'status': u'ok'},
 u'state': u'running'}
```
