## How to render images using Headless Blender
This allows us to use Blender from the command-line. Headless means no blender ui is opened and all commands to the blend file have to be made through command-line commands which are explained here

### Need:
Setting up the `blender`command line command: [https://docs.blender.org/manual/en/latest/advanced/command_line/launch/index.html#command-line-launch-index](https://docs.blender.org/manual/en/latest/advanced/command_line/launch/index.html#command-line-launch-index)

Running blender via command line: [https://docs.blender.org/manual/en/latest/advanced/command_line/render.html](https://docs.blender.org/manual/en/latest/advanced/command_line/render.html)

## Blender Command line Arguments
A common blender command line call can look like the following. 
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

If you want to render to a specific output path you have to add the path to the terminal command like the following.
``` Terminal
blender -b Documents/Blender/headless_test/cube1.blend -o Documents/Blender/Renders/frame_##### -E CYCLES -f 10
```
-  `-o` 
	- output path
- `frame_#####` 
	- enumerates each rendered frame counting up
-  `-E CYCLES`
	- Sets the render engine to cycles. Default is what the file is using

When you want to load a script that runs with the Blender file you have to add it to the command like the following.
```Terminal
blender -b "$BLEND_FILE" -P "$SCRIPT_FILE"
```

### Headless Example:
In our case we want to render our images with a script that starts the renderings, switches configurations and then renders the next image. Our basic render call looks like the following:
```
blender -b <path-to-.blend> -P <path-to-script> 
```
Our script has optional arguments that work like Blenders optional arguments. These options are added at the end of the Terminal call. 

- `test` no pictures are rendered only file paths are logged and amount of files are counted
- `test-rend` renders pictures in human viewable format
- `min` only first picture for every camera is rendered
- `pre` renders are in low resolution

To test if the script is working clone the remote: `git clone https://<your-name>@bitbucket.org/weiseundstark/ansible-server-management.git`. Then put the newest 964 Blender file into the blender_files folder you just cloned. Then you can run these commands from your Visual Studio Code Terminal or from your own Terminal at `cd ansible-server-management`.

964_ext: Renders in TEST_MODE
```Terminal
blender -b roles/blender_scripting/blender_files/964_ext_206.blend -P roles/blender_scripting/files/964_ext.py test
```
964_int: Renders in MINIMUM_MODE + PREVIEW_MODE
```Terminal
blender -b roles/blender_scripting/blender_files/964_int_173.blend -P roles/blender_scripting/files/964_int.py min test
```
g_ext_early: Renders in MINIMUM_MODE + PREVIEW_MODE
```Terminal
blender -b roles/blender_scripting/blender_files/g_ext_31.blend -P roles/blender_scripting/files/g_ext_early.py test min
```