---
title: MultiChat
year: 2018
published: true
tags: ['javascript']
series: false
cover_image: ./images/multichat.jpg
canonical_url: false
description: "Experimental P2P discussion app using graphs and local storage"
---

[Source code](https://github.com/Nirgalz/multiChat)

Experiment to see how graphs could help make discussions less linear than in traditional forums, chats, etc...

It uses webRTC to make communications P2P, it just needs a simple node server that serves as a listener.
PouchDB is used as local storage, meaning conversations are stored on clients instead of on the server.

![alt text](./images/multichat2.jpg "contextual menu")
