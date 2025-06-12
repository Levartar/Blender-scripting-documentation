Blender allows us to use Blender scripts within the .blend file. These scripts are run in an internal Python component that has no access to you file system. This means you cant import scripts within scripts normally!

## Loading scripts headless
In an example i have a scripts folder for a cube.blend file that wants to import scripts
```
your_project/
├── cube.blend
└── scripts/
    ├── mainscript.py
    └── importscript.py
```

Importing headless works perfectly using
```
blender -b  cube.blend -P scripts/mainscript.py
```
mainscript.py imports importscript.py for helperfunctions.

### The Problem
Opening mainscript.py in the Blender scripting editor and running it throws an error because Python cant find the file. To solve this a switch has to be added to the code that recognises both methods of launching the script.

## Multiplatform script loading solution
```Python
# Try to detect the directory this script is in
if "__file__" in globals() and os.path.isfile(__file__):
	# Running headless
	script_dir = os.path.dirname(__file__)
else:
	# Running from Blender's scripting tab
	script_dir = bpy.path.abspath("//scripts")
if script_dir not in sys.path:
	sys.path.append(script_dir)
	
print("Script dir:", script_dir)
```