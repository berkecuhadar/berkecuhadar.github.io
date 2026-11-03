---
title: Script2Markdown
date: 2026-11-03
status: Extension
tags: [VS Code, C#, Unity, LLM]
summary: A VS Code extension that bundles all C# files in a folder into a single Markdown file, ready to paste into an LLM.
image: /src/img/labs/script2markdown.png
image_caption: Right-click a folder in the VS Code Explorer to export it.
---

Giving an LLM a whole Unity project usually means copying scripts one by one. Script2Markdown does it with one right-click: it scans a folder for C# files and writes them into a single Markdown file.

It works for any C# code base (Unity, Godot, .NET), whenever you want a model to review, debug or refactor more than one file at a time.

Links: [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=berkecuhadar.script2markdown) · [GitHub](https://github.com/berkecuhadar/script2markdown)

## What it does

- Exports from the VS Code Explorer with a right-click on a folder.
- Scans subfolders recursively and collects every `.cs` file.
- Uses each file's relative path as its heading, for example `Scripts/Player/Movement.cs`.
- Wraps every file in a `csharp` code block.
- Opens a save dialog, with `Script2Markdown_Output.md` as the default name.

## How to use it

1. Open your C# project in VS Code.
2. Right-click the folder that holds the scripts.
3. Run **Script2Markdown: Export C# to MD**.
4. Pick where to save the file.

## Output

~~~markdown
# Script2Markdown Export

## Player/PlayerController.cs

```csharp
// file contents
```
~~~

## Install

Search for "Script2Markdown" in the Extensions view, or run `ext install berkecuhadar.script2markdown` in Quick Open. The extension is MIT licensed.
