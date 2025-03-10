---
description: ' Use the Open 3D Engine console variables (CVARs) to debug your cinematic
  scenes. '
title: Debugging Cinematic Scenes with Console Variables
---

{{< preview-migrated >}}

You can specify the following console variables when profiling a scene. For more information, see [Using the Console Window](/docs/user-guide/editor/console.md).


**Cinematic Scene Console Variables**

| Console Variable | Description | Valid Values |
| --- | --- | --- |
| e\_DisplayInfo |  Displays basic performance information. The console variable also displays a warning if you exceed texture streaming memory.  |  `0` = Off `1` = On `2` = Enhanced `3` = Compact  |
| p\_profile\_entities |  Runs your scene and looks for fluctuations. You can use this console variable to identify which entities are causing large peaks.  |  `0` = Off (default) `1` = On   |
| r\_Stats |  Toggles render statistics. Specify a value of `6` to finds assets with large draw calls or excessive materials.  For example, this can help you find where shadows can be disabled, and so on.  |  `0` = Off `1` = Displays per-frame and global render statistics. `2` = Displays shaders for selected object. `3` = Displays the CPU times for render passes and video memory usage. `4` = Displays CPU times for render passes only. `5` = Displays occlusion query calls. `6` = Displays per-instance draw call count. `8` = Displays information about the total number of instances and batches. `13` = Displays information about cleared render targets.  |
| e\_DebugDraw |  Displays helpers with information for each object. Specify a value of `2` to display polycount. Specify a value of `3` to display the current level of detail ([LOD](/docs/user-guide/appendix/glossary#lod)) for the selected entity. For example, in the console window you can enter the following command:  e\_DebugDraw 2 \| 3  |   `1` = Name of the used `.cgf` file, polycount, and used LOD.  `2` = Displays color coded polygon count.  `3` = Displays color coded LODs count. Flashing colors indicate a single LOD.  `4` = Displays object texture memory usage.  `5` = Displays color coded number of render materials.  `6` = Displays ambient color.  `7`= Displays triangle count, number of render materials, and texture memory `10` = Renders geometry with simple lines and triangles `13` = Displays occlusion amount.   This can take a long time to calculate, depending on level size.   `15` = Displays exported helpers. `16` = Displays the debug gun. Select an object for more information. `17` = Displays streaming information (buffer sizes). `19` = Displays physics proxy triangle count for each object. `20` = Displays the texture memory usage for character attachments. `21` = Displays an animated object distance to the camera. `22` = Displays an object's current LOD vertex count. `23` = Displays an object in red if it's casting a shadow. `24` = Displays objects with 0 LOD with red text. `25` = Display objects with 0 LOD with red text and objects with 1 LOD with blue text.  |
| e\_CameraFreeze |  Locks your current view, so that you can look around without redrawing any elements. You can use this console variable to locate problems and fix them, such as object culling and LOD. The view frustum is drawn in a white frame.  |  `0` = Off (default) `1` = On   |
