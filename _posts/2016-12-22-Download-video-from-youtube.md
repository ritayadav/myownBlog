---
title:  "Download video from youtube in UBUNTU (Linux)"
header:
  teaser: https://c4.staticflickr.com/1/754/31801541395_6f9d2e0f36_b.jpg
  og_image: https://c4.staticflickr.com/1/754/31801541395_6f9d2e0f36_b.jpg
modified: 2016-12-22T16:03:49-04:00
categories: 
  - Linux
tags:
  - Youtube
  - Ubuntu
---

### Step 1: Open a terminal with `Ctrl`+`Alt`+`T` or searching Terminal in the dash.

### Step 2: Install `youtube-dl` with this command (you'll be prompted for your password):

`sudo apt-get install youtube-dl`

### Step 3: Seach video from youtube and copy the url of video.

`youtube-dl  -F https://www.youtube.com/watch?v=VwvHeFixpZY`

{% include figure image_path="https://c4.staticflickr.com/1/754/31801541395_6f9d2e0f36_b.jpg" alt="this is a placeholder image" caption="List of video quality." %}
It shows the list of video quality available for that video.

### Step 4: paste the url in Terminal as

`youtube-dl  -f 22 https://www.youtube.com/watch?v=VwvHeFixpZY`
{% include figure image_path="https://c8.staticflickr.com/1/302/31801565015_142354dfcd_b.jpg" alt="this is a placeholder image" caption="Downloaded video." %}

### Step 5: Go to download folder

You can see there your downloaded video.

## Check out this video for more information
<iframe width="560" height="315" src="https://www.youtube.com/embed/4Uxb6iQMEu0" frameborder="0" allowfullscreen></iframe>



Thanks!
