# Getting Started

Before you start working on this a warning. This script has not been properly planned and most features are only finished to the bare minimum and are not resilient at all. Its probably better to rewrite this from scratch. This documentation is unfinished.

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

### [files/](Files.md)
main folder where scripts are stored

### [helpers](Helpers.md)/
universal script helpers