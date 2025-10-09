# Getting Started

If not already done clone the repository 

```git clone https://<your-name>@bitbucket.org/weiseundstark/ansible-server-management.git```

After that download the Blender files from this [sharepoint](https://weiseundstark.sharepoint.com/sites/elferplatz/Freigegebene%20Dokumente/Forms/AllItems.aspx?id=%2Fsites%2Felferplatz%2FFreigegebene%20Dokumente%2FGeneral%2F3D%20Share%2FBlender%2DFiles&viewid=77e29346%2D5cca%2D440b%2D86ad%2Dd4308210cb0f&ct=1744795891166&or=Teams%2DHL&ga=1&noAuthRedirect=1)

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

### blender_files/
The Blender files are not uploaded to the repo and are saved on a [sharepoint](https://weiseundstark.sharepoint.com/sites/elferplatz/Freigegebene%20Dokumente/Forms/AllItems.aspx?id=%2Fsites%2Felferplatz%2FFreigegebene%20Dokumente%2FGeneral%2F3D%20Share%2FBlender%2DFiles&viewid=77e29346%2D5cca%2D440b%2D86ad%2Dd4308210cb0f&ct=1744795891166&or=Teams%2DHL&ga=1&noAuthRedirect=1). Download the Blender files and copy them into your blender_files directory.

### [files/](Files.md)
main folder where scripts are stored

### [helpers](Helpers.md)/
universal script helpers