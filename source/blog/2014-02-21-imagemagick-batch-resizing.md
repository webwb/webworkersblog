---
title: Image Batch-Resizing with ImageMagick
date: 2014-02-21 
category: code
tags: [cli, imagemagick]
---

	convert face*.png -adaptive-resize 100x100 -set filename:f "%t_100x100" "%[filename:f].png"

