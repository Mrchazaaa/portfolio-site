---
title: "Procedurally Generated Clouds"
date: 2024-03-04
description: "I embedded a standalone p5.js sky sketch as an isolated static scene inside this blog."
pageNumber: "202"
---

I originally built this animated sky scene during university and recently refactored it into a small standalone static project. It now lives as plain HTML, CSS, and JavaScript, which makes it much easier to reuse without dragging a larger app structure in behind it.

{{< sketchframe src="sketches/sky-p5/index.html" title="Sky p5.js sketch" height="340px" >}}

For this version of the post I kept the sketch isolated and served it as its own static bundle inside the Hugo site. That means the blog page does not need to load the sketch's CSS into the teletext theme or share runtime state with the sketch itself.

I still find that kind of reduction useful. A lot of engineering work gets buried under framework structure, deployment details, and product constraints. Pulling out the smallest interesting part is a good way to check whether the core idea is actually solid and whether it can survive outside the original project it came from.

This sketch is a good example of how I tend to work on side projects: build broadly enough to explore, then come back later and separate the durable parts from the scaffolding around them.
