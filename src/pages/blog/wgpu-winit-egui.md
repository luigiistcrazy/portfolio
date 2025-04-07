---
layout: ../../layouts/BlogLayout.astro
title: Egui with WGPU + Winit
description: Easily integrate Egui with your existing WGPU + Winit codebase
tags: ["rust", "WGPU", "Winit", "Egui", "GUI", "open-source"]
time: 69
timestamp: 2025-04-08T00:00:00+02:00
featured: true
filename: wgpu-winit-egui
---

## Intoduction

When you're developing graphics intense software, such as a game engine, debugging and monitoring performance becomes one of the top priorities.

As FeXun became more and more complex and there were a lot of things going on in singular scenes, we were suddenly limited by Mangohud's and RTSS's (RivaTuner Statistics Server) limited metrics. We didn't have a proper way to look deep into the engine during runtime.

We initially tried postponing GUI development as much as possible. We know we would have a terrible time getting things to work. There are multiple reasons why websites like [AreweGUIYet?](https://areweguiyet.com/) exist.


