---
layout: ../../layouts/ProjectLayout.astro
title: Cargo-Rush
description: A remote build, test, and run tool for Cargo. Why compile locally when your powerful remote machine can do the heavy lifting?
tags: ["WIP", "rust", "cargo", "open-source"]
githubUrl: https://github.com/luigiistcrazy/cargo-rush
timestamp: 2025-04-07T19:00:00+02:00
featured: true
filename: cargo-rush
---

## Overview

**cargo-rush** lets you build, test, and run your Rust code on a remote machine with ease. It keeps everything in sync between your local and remote environments using `rsync`.

> **Note**: cargo-rush is still in active development and not ready for production use — yet. But I'm working on it constantly because, frankly, I really need it myself.

## The Idea

A few weeks ago, I was sitting in school, working on my [game engine](https://luis.weitl.xyz/projects/fexun). When I’m not at home, I use my laptop — which I absolutely despise. It’s a slow, clunky Acer convertible with barely any processing power. It’s fine for school work, but try compiling 300 crates in release mode on it.

Even a basic debug build (with dependencies cached!) takes at least 30 seconds. A full recompile in debug mode? That’s 10 minutes, easy.

It. Is. Slow.

But then I thought...

Wait, I have a really powerful PC running Arch Linux™ at home. Why not use that to handle compilation and just send the compiled binary back to the laptop? That way, I can take advantage of my desktop’s power without torturing my poor Celeron.

## The Execution (Sort of)

Here’s how the final product will work:

First, you initialize cargo-rush in the root of your Rust project:

```sh
cargo rush --init
```

This creates a `.cargorush.toml` config file in the project root and, if a `.gitignore` is present, it automatically adds the config to it for convenience.

The `.cargorush.toml` file holds project-specific settings, like:

General info: project name, path, Rust version

Remote info: name, address, remote path, target platform

You can edit this file manually, or use the CLI. I want cargo-rush’s commands to feel familiar — think Git-style syntax.

### Configuring a Remote

```sh
cargo rush remote add name user@address    # adds a remote
cargo rush remote remove name              # removes a remote
cargo rush remote list                     # lists remotes for the current project
```

Once your remote is configured, you can start building with cargo-rush. It only syncs the necessary files and only transfers the final binary back to your machine. On the next build, only modified files get re-synced.

If you don’t specify a remote path, cargo-rush uses a temporary directory—`/tmp` on Unix-like systems or `C:\Users\YourName\AppData\Local\Temp` on Windows. It figures this out using Rust’s built-in `std::env::temp_dir()`.

### Starting a Build

```sh
cargo rush build        # builds on the remote
cargo rush build -r     # builds in release mode
cargo rush clippy       # runs Clippy
cargo rush test         # runs tests
```

All of the above commands run just like they would locally. You’ll still see Cargo’s familiar output after each command—just as if you were running it on your own machine.

## Afterword

Of course, these aren’t all the features I plan to add. If you have ideas, suggestions, concerns, or just want to chat—feel free to reach out on GitHub, Bluesky, or wherever. I really appreciate any kind of feedback.

I’m aiming to have this mostly done and stable by the end of summer 2025.

Cheers!
