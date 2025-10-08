# Getting Started

Before you start working on this a warning. This script has not been properly planned and most features are only finished to the bare minimum and are not resilient at all. Its probably better to rewrite this from scratch. 

Only the mad may enter the monolith 

## Files
```
ansible-server-management/
├── ***
└── roles/
    ├── ***
    └── blender_scripting/
        ├── blender_files/
            └──  blender files.blend
        └── files/
            ├── ***
            ├── 964_ext.py
            ├── 964_int.py
            ├── f_ext.py
            ├── f_int.py
            ├── g_ext.py
            ├── g_int.py
            └── helpers/
                ├── cloud_config.py
                ├── cloud_helpers.py
                ├── render_settings.py
                ├── shared_colors.py
                └── shared_helpers.py/
```

### blender_scripting/
blender files are copied here when the script runs on the build server

### files/
main folder where scripts are stored

### helpers/
universal script helpers

### Solving the Problem
Because of this we are not rendering each combination individually we only render each single part with each combination and combining them in post. 
![Reflections](docs/assets/reflections.png)
This way we still render the same amount of pixels but we can remove redundant images if they do not affect each other. For example: if the rims change color the headlights don't need to render again. 
Now we can create dependency tables that show which part can affect the rendering of another part and which part can be rendered independently. 