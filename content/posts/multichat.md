---
title: MultiChat
year: 2018
published: true
tags: ['experiment','javascript','P2P','graphs']
series: false
cover_image: ./images/multichat2.jpg
canonical_url: false
description: "Experimental P2P discussion app using graphs and local storage"
---

[Source code](https://github.com/Nirgalz/multiChat)

Experiment to see how graphs could help make discussions less linear than in traditional forums, chats, etc...
It uses webRTC to make communications P2P, it just needs a simple node server that serves as a listener.
PouchDB is used as local storage, meaning conversations are stored on clients instead of on the server.

![alt text](./images/multichat.jpg "contextual menu")

This only serves the purpose of a proof of concept.
What we learnt through this will help to make a really usable application offering a different discussion experience.
I'll get back to it when I have enough time and resources.
