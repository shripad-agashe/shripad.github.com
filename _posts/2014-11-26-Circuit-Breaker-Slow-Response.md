---
layout: post
title: "Circuit breaker is about slow response"
date: 2014-11-25 16:25:06 -0700
comments: true
categories: {"performance", "latency", "soa"}
---


In his seminal book [Release It!][ri] Michael Nygard ellicited the "Circuit Breaker" pattern. He documented the pattern as one of the fundamental stability pattern. However he did not give any implementation schematic and also the documentation does not go in depth about the logic and fundamental need for this pattern. As mentioned in the book, circuit breaker pattern is for preventing cascading failures, unbalanced capacities, slow responses. But most often, it is coupled only with timeout tracking. In his blog about [Circuit Breaker][cb] Martin Fowler also referred this pattern only for tracking failures. I think using circuit breakers only in case of failures is inappropriate at least from a logical perspective if not implementation perspective.

Response time and timeout
===
In some sense, timeouts can be viewed a class of errenous responses. With this view point, timout is a case of extremly slow response. If the remote service starts returning responses with latency close to timeout, circuit breakers which track timeout errors would be unable to guard against remote services. The effect of slow response is almost similar to a timeout case.


[cb]:http://martinfowler.com/bliki/CircuitBreaker.html
[ri]:http://www.amazon.com/gp/product/0978739213?ie=UTF8&tag=martinfowlerc-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0978739213
