---
title: Ludograph
date: 2026-11-02
status: Tool
tags: [Game Design, MDA, Onion Model, React, TypeScript]
summary: A web-based diagram editor for game design. Draw mechanics, dynamics and aesthetics as typed nodes and edges, and let the tool check the graph and suggest what to work on next.

image: /src/img/labs/ludograph.png
image_caption: The Ludograph editor.
---

Game design documents tend to be walls of text, and diagrams drawn in a general-purpose tool cannot tell you when something is missing. Ludograph is a diagram editor made for game design. You draw the design as a graph of typed nodes and edges, and the tool checks it for you.

It runs entirely in the browser, with no backend. Work is autosaved in local storage and can be saved to and opened from `.ludograph.json` files.

<a href="https://ludograph.mythlorestudios.com" target="_blank" rel="noopener" class="btn btn-primary btn-sm"><i class="bi bi-box-arrow-up-right"></i> Try it live</a>

Source code: [github.com/berkecuhadar/ludograph](https://github.com/berkecuhadar/ludograph)

## Where the ideas come from

- **MDA** (Hunicke, LeBlanc, Zubek): mechanics, dynamics, aesthetics. You write the mechanics, players experience the aesthetics. Ludograph tries to make the chain from one to the other easy to draw and to check.
- **The Onion Model** by Paolo Tajè: mechanics are arranged in layers, from the core mechanic outward.

Added by Ludograph itself: the rule that an inner layer should still work without the outer ones (a warning you can switch off), the Design Path panel, core-only prototype mode and the validation rules.

## What it does

- **Typed nodes and edges:** pillar, aesthetic, persona, dynamic, mechanic, state, rule, resource and more, plus your own kinds. Edges such as feeds, requires, unlocks, triggers, modifies, conflicts, leads to and serves, with rules about what may connect to what.
- **Drill-down:** double-click a node to open the graph inside it.
- **Design Path panel:** works outside-in or core-first, with a core-only prototype mode.
- **Validation panel:** 16 checks on the graph.
- **Document view:** the written game design document, based on [OpenGDD](https://github.com/berkecuhadar/opengdd). It can pull text from the graph.
- **Export:** Markdown (a GDD), Unity JSON, PNG and SVG.

## Three views of the same data

- **Graph:** free layout.
- **Onion:** four rings. Drag a node into a ring to change its layer.
- **MDA:** three lanes. Selecting an aesthetic lights up the mechanics that lead to it.

{% include media.html image="/src/img/labs/ludograph.gif" alt="Graph, Onion and MDA views" caption="The Graph, Onion and MDA views" %}

## Working with a Unity project

Ludograph can fill the graph from your C# code, in the editor or on the command line. It reads MonoBehaviours, ScriptableObjects and state enums, makes a node for each and adds `requires` edges from `[RequireComponent]`. Scanning again updates the nodes and never overwrites text you wrote.

- **In the editor:** File > Import from Unity code. Files are read in the browser and not uploaded, and undo takes the import back.
- **On the command line:** a small tool adds and checks nodes and edges in a project file and can scan a Unity project.
- **With Claude Code:** a skill file lets Claude read your code, propose layers and edges, and write them through the command line tool, which refuses invalid ones. Ludograph itself makes no AI calls and needs no key.

```sh
ludograph init design/game.ludograph.json --name "My game"
ludograph scan-unity design/game.ludograph.json Assets --dry-run
ludograph validate design/game.ludograph.json
```

## Built with

React, TypeScript and Vite, with React Flow for the canvas, dagre for layout and Zustand for state. The project is MIT licensed.

## Next

Maybe resource-flow simulation, in the spirit of Machinations, and Turkish text for the interface.
