---
layout: post
title:  "Escaping backslash in $http_proxy"
date:   2013-02-14 22:17:04 +0800
categories: note-to-self
---
I recently had to connect to github using https because the client I'm working for has locked down outbound ssh access. I knew about the bash shell variable $http_proxy for a long time but somehow I couldn't get it to work this time. It turned out that the backslash between the AD domain and my user id is the culprit.

To put in user ids such as swdev\kyeung in $http_proxy, the syntax is ```http_proxy=http://swdev%5Ckyeung@proxy.enterprise.inc:8080```
