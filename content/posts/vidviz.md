---
title: VidViz
year: 2020
published: true
tags: ['java','spring','vuejs']
series: false
cover_image: ./images/vidviz2.jpg
canonical_url: false
description: "Video assets management tool"
---

Developed specifically for a VFX designer to facilitate his workflow, but generalist enough to be used in various cases where one wants to visualize and control multiple videos at the same time, or simply better manage a video library.
As of now, it is primarily designed to be used as a local tool.

### features :
##### Videos :
* Control multiple videos at once : play/pause, video speed, auto-loop, show/hide controls.
* Select/unselect. 
    * Hide/view videos
    * Download videos associated json files. 
    * Delete videos and json files.
* Contextual menu to open file in system browser or download json.

##### Files :
* Upload files or use them directly using the file system. The app will update its content.
* Upload json files associated with each video to get the metadata of that video you selected.
* Automatic encoding of video thumbnails for better encoding experience.
* Search, filter, edit and delete your folders.
![alt text](./images/vidviz.jpg "contextual menu")
### possible evolutions
* Online version with security
* SAAS service
...

The source code isn't open source yet as I'm figuring out what's next.
