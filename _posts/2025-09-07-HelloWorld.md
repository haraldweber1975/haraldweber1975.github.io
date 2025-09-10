---
title: Hello World!
date: 2025-09-07 14:54:00 +0200 #CET Summer Time
description: Another hello world article...
categories: [Story]
tags: [info]     # TAG names should always be lowercase
---

Another hello world article, as I recently started over with my blog.  
I lost a couple of outdated articles, but I don´t care about it.

Updating the several years old theme, I run into issues and decided to try out something new.

After asking Google Gemini (which is to date still the best option to use AI on a free plan)  
I tried out [Chirpy](https://github.com/cotes2020/chirpy-starter).

By the way - the last re-launch of my private webpage was without any AI help.  
This really makes a **huge** difference in research and troubleshooting.

Might be a good follow-up post: How AI changed my "learning by doing" approach :)

See you soon!  
Harald

<p>Your public IP address is: <span id="public-ip">Loading...</span></p>

<script>
  fetch('https://api.ipify.org?format=json')
    .then(response => response.json())
    .then(data => {
      document.getElementById('public-ip').textContent = data.ip;
    })
    .catch(error => {
      console.error('Error fetching IP:', error);
      document.getElementById('public-ip').textContent = 'Unable to fetch IP';
    });
</script>
