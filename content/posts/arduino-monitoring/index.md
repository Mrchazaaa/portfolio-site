---
title: "Arduino And LoRa Monitoring System"
date: 2023-01-11
description: "A low-power Arduino sensor node that reports rehearsal room conditions to a Raspberry Pi over LoRa."
pageNumber: "207"
---

I built this project because I wanted a better picture of what was happening in the drumming practice space I rent. In particular, I wanted to know when the room was being used and what the environmental conditions were like over time, but the space had no Wi-Fi and I did not want to rely on mains power just to gather a few sensor readings. That made it a much more interesting systems problem than a normal Arduino logging project.

{{< imagepair
  leftSrc="ArduinoMonitoring.jpg"
  leftAlt="The Arduino monitoring hardware with sensors and radio module"
  rightSrc="charts.png"
  rightAlt="Charts showing the environmental data collected from the practice space"
>}}

The sensing node is built around an Arduino Pro Mini 3.3V with sensors for PIR motion, humidity, temperature, and ambient light. Every cycle it wakes up, collects readings, packs them into a small JSON payload, transmits the result by radio, and then goes back to sleep for ten minutes. I spent a fair amount of effort on power reduction so the device could run for roughly six months from three AA batteries, which mattered more to me than squeezing in more frequent readings.

The lack of Wi-Fi in the space is what pushed the project in a direction I like. Instead of uploading data directly, the Arduino sends it over LoRa to a Raspberry Pi receiver around 2km away in an urban environment. The Pi then handles the more network-heavy side of the system: receiving the packets, logging them, and forwarding the data onwards to services like ThingSpeak. That split kept the sensing node simple and power-efficient while still giving me a proper pipeline for storing and inspecting the data.

I like this project because it combines embedded constraints with a slightly more operational mindset. It is not just a sensor board taking measurements; it is a small monitoring system with battery life concerns, radio communication, remote ingestion, and useful visualisation at the end. The result is fairly modest, but it solved a real problem for me and it is a good example of the kind of practical, end-to-end engineering work I enjoy.

[View the project on GitHub](https://github.com/Mrchazaaa/arduino-monitoring)
