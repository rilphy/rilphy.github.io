---
layout: post
title: "Day 117: Parsing a JSON File and Fixing Broken Korean Text"
date: 2025-09-27 00:52:43 +0900
categories: [Game Development, Visual Novel]
tags: [Unity, JSON, TextMeshPro, Korean font]
toc: true
toc_sticky: true
description: "Displayed dialogue by parsing a JSON file, and fixed broken Korean text in TMP by changing the font atlas size."
---

I made a simple JSON file and a simple parser for it.

Unity has a built-in feature for this, so the code wasn't long, and I put it together quickly by following a blog.

For now, I'm only displaying the dialogue. Advancing to the next line, showing the character name, showing character illustrations, and choices are lower priority.

![Dialogue output result](https://blog.kakaocdn.net/dna/dmqqbU/btsQTjAnQrj/AAAAAAAAAAAAAAAAAAAAAKH8gevvXMw3JPkjw_0EP_OKEjirN4ou4R68UkpKNpzf/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1793458799&allow_ip=&allow_referer=&signature=npZW300%2F4b9%2FJQMbBO9PFcHctzY%3D)

The text displayed successfully, but the Korean font was broken. I had added a separate Korean font and it still came out broken, so I wondered what the cause was.

![Font atlas settings](https://blog.kakaocdn.net/dna/bk0IqX/btsQShDAVri/AAAAAAAAAAAAAAAAAAAAAFKHyPPmgvzqEQt1PJVGenRjZiatiBBFMcJb_uhgDsux/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1793458799&allow_ip=&allow_referer=&signature=dpx%2BNh%2BIQbfGUB9Jj9TXwWOifM0%3D)

The font atlas size was the problem. It has to be set to 4096 like in the screenshot, or the text breaks. It was originally 512. It also seems better to change Atlas Population Mode from Static to Dynamic.

![Correct output after the fix](https://blog.kakaocdn.net/dna/I4xr6/btsQTksyX8G/AAAAAAAAAAAAAAAAAAAAAHymT9Qm1MDWtA1yoGDI5x_eDP1Ku34Getk9J5B9jwTX/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1793458799&allow_ip=&allow_referer=&signature=TJ%2F22PZzNGOsWkkvB32%2B0D9dEJ4%3D)

After the fix, it runs and displays correctly. Tomorrow I'll work on displaying the other lines too, advancing to the next line with the spacebar, showing character names, and adding choices and branching.
