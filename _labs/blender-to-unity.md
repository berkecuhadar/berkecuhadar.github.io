---
title: Blender to Unity
date: 2026-11-03
status: Add-on
tags: [Blender, Unity, FBX, Pipeline]
summary: A Blender add-on that exports selected objects as Unity-ready FBX files with one-click presets for static meshes, rigs and animations.
image: /src/img/labs/blender-to-unity-ui.png
image_caption: The To Unity FBX panel in Blender's sidebar (press N).
---

Exporting from Blender to Unity means the same settings every time: axis orientation, scale, baked transforms, leaf bones on rigs. One wrong checkbox and the model arrives rotated, scaled wrong or with extra bones. This add-on puts those settings behind a few buttons so the export is the same every time.

Source code: [github.com/berkecuhadar/Blender_to_Unity](https://github.com/berkecuhadar/Blender_to_Unity)

## What it does

- **Three one-click presets:** Static Mesh, Rigged (no animation) and Rigged + Animations.
- **Custom Export** for when the presets are not enough.
- **Unity-friendly axes:** -Z forward, Y up.
- **Clean rigs:** leaf bones are removed and only deform bones are exported.
- **Baked transforms** for meshes and armatures.
- Works with **Blender 4.0 and newer**, targets **Unity 6**.

## How to use it

1. Zip the `to_unity_fbx` folder (the folder itself must be inside the archive).
2. In Blender, open *Edit > Preferences > Add-ons*, click *Install*, pick the zip and enable **To Unity FBX**.
3. Press **N** in the 3D viewport and open the **To Unity FBX** tab.
4. Select your objects and click a preset.

## Re-exporting without breaking Unity

Export the first time straight into the project's `Assets` folder. After that, every export overwrites the same file with the same settings, so Unity keeps the same GUID and nothing that references the model breaks.

## Example workflow with Mixamo

1. Export the character from Blender with the *Rigged* preset.
2. Upload it to Mixamo and pick animations.
3. Import the animated file back into Blender.
4. Export again with the *Rigged + Animations* preset and drop it into Unity.

## Notes

Only mesh and armature objects are exported. The add-on is MIT licensed.
