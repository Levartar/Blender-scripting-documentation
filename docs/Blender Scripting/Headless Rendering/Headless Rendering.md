## How to render images using Headless Blender
This allows us to use Blender from the command-line. Headless means no blender ui is opened and all commands to the blend file have to be made through command-line commands which are explained here

### Need:
Comand Line Blender Launch:
https://docs.blender.org/manual/en/latest/advanced/command_line/launch/index.html#command-line-launch-index

### Blender Terminal Rendering Command:
https://docs.blender.org/manual/en/latest/advanced/command_line/render.html

min usable:
```
blender -b file.blend -f 10
```
- `blender` 
	- blender headless launch command
-  `-b` 
	- render in background
-  `file.blend`
	- path to file that renders
-  `-f 10`
	-  render the 10th frame (required!)

render to specific output path:
``` Terminal
blender -b Documents/Blender/headless_test/cube1.blend -o Documents/Blender/Renders/frame_##### -E CYCLES -f 10
```
-  `-o` 
	- output path
- `frame_#####` 
	- enumerates each rendered frame counting up
-  `-E CYCLES`
	- Sets the render engine to cycles. Default is what the file is using

Headless Script Loading
```Terminal
blender -b "$BLEND_FILE" -P "$SCRIPT_FILE"
```

### Headless Example:
Elferplatz script Headless rendering Usage:

Basic call: Renders in full Size
```
blender -b <path-to-.blend> -P <path-to-script> 
```
Options:
Options are added at the end of the Terminal call
- `test` no pictures are rendered only file paths are logged and amount of files are counted
- `test-rend` renders pictures in human viewable format
- `min` only first picture for every camera is rendered
- `pre` renders are in low resolution

Example calls
964_ext: Renders in TEST_MODE
```Terminal
blender -b Documents/mass-rend-test/964_ext_206.blend -P Documents/w-s/ansible-server-management/roles/blender_scripting/files/964_ext.py test
```
964_int: Renders in MINIMUM_MODE + PREVIEW_MODE
```Terminal
blender -b Documents/mass-rend-test/964_int_173.blend -P Documents/w-s/ansible-server-management/roles/blender_scripting/files/964_int.py min test
```
g_ext_early: Renders in MINIMUM_MODE + PREVIEW_MODE
```Terminal
blender -b Documents/mass-rend-test/g_ext_31.blend -P Documents/w-s/ansible-server-management/roles/blender_scripting/files/g_ext_early.py test min
```
