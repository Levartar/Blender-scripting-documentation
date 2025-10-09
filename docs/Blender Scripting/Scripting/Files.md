# Files

This folder consists of different scripts that individually run all configurations for a specific car exterieur and interieur.


## Scripts Overview
All scripts fundamentally work the same. They are made up of 1. A definition for this blender files specific variables. 2. Render Loop commands 3. A call to render all.

### File Specific Definitions
This is the most time consuming part of the script and modifying these need extensive knowledge of the script and rendering pipeline or communication with the ones responsible.

Explanation of the variables:

`OUTPUT_TEMPLATE = ("./B01/E_Ext/E_{layer}/M{model}-{antrieb}-{bodykit}/.."`
A file storage template. Each `{var}` gets regex replaced with the values the part is set to. Its important to communicate any changes made to this as the frontend relies on this path exactly to get their images.

| `OUTPUT_TEMPLATE = ("./B01/E_Ext/E_{layer}/M{model}-{antrieb}-{bodykit}/.."` | 
| ---------------- | 
| A file storage template. Each `{var}` gets regex replaced with the values the part is set to. Its important to communicate any changes made to this as the frontend relies on this path exactly to get their images. | 

| `path_pattern = ["P","FL","V",.."` | 
| ---------------- | 
| Keys used for replacing the corresponding output template `{var}`| 

| `CAMERAS_TO_RENDER = ["C1","C2",..` | 
| ---------------- | 
| List of all Camera names as they are named in Blender that should be rendered| 

| `LOOPS_TO_RENDER = ["Hintergrund","Bremsen",..` | 
| ---------------- | 
| List of all render loops. A render loop is responsible for rendering all configurations a ex. `Hintergrund` can have. Commented out to skip. See more at CFS| 

| `set_render_settings()`| 
| ---------------- | 
| [see helpers](Helpers.md#render-settings) |


| ```cameras = {"CamsBG": [cam for cam in ["C1", "C2", "C3", "C4", "C5", "C10"] if cam in CAMERAS_TO_RENDER],..```| 
| ---------------- | 
| Defines the group of cameras that are rendered to show a specific feature |

| ```light_setups, glass_setups```| 
| ---------------- | 
| Depending on the camera switches the Light or Glass for a better render image |

| ```BGColors, Models,..```| 
| ---------------- | 
| Feature mapping for the Blender file. Each value can be mapped to the corresponding blender datapath to change a configuraion. See more at CFS |

| ```CFS```| 
| ---------------- | 
| Central Feature Switch table: name -> (data_path, mapping_dict) |

| ```georefresh_objects```| 
| ---------------- | 
| Objects needing a force refresh after parameter changes |

| ```get_render_constants()```| 
| ---------------- | 
| Return core constants passed into render_scene_with_config |

### Render Loop Commands
Each function prepares scene state (node / modifier sockets) then calls `render_scene_with_config()` with: loopKey, camera list, folder key, configurations, slot mapping, and a short variant code. Each loop is defined like:

```Python
def <name>():
    """Render Loop dependent variations."""
    bpy.data.objects["Car_Instancer_Base"].modifiers["GeometryNodes"]["Socket_4"] = 0 # Set socket needed for Loop

    configurations = [ # Features that should generate all possible configurations out of all of their combined possible combinations
        CFS["Bodykits"],
        ...
    ]

    slot_mapping = { # Used to generate the Path and keeping all images unique
        "bodykit": 0,
        ...
    }

    render_scene_with_config( # Main render call
        "<name>",
        cameras["<CamsName>"],
        "<name>",
        configurations,
        slot_mapping,
        "E0",
        *get_render_constants()
    )
```


### 964_ext.py
964 exterieur script used with 964_ext_***.blend. Main file with newest changes. All other files are only a copied version of 964_ext with adjusted vars.

### 964_int.py
964 interieur script used with 964_int_***.blend.

### f_ext.py
F model exterieur script f_ext_***.blend.

### f_int.py
F model interieur script used with f_int_***.blend.

### g_ext.py
G model exterieur script g_ext_***.blend.

### g_int.py
G model interieur script used with g_int_***.blend.