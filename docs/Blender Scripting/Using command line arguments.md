## How Blender Scripting System Arguments work
sys args contain all additional arguments when a program is called from the command line

```python
import sys
argv = sys.argv
argv = argv[argv.index("--") + 1:]  # get all args after "--"

print(argv)  # --> ['example', 'args', '123']
```

```Terminal
blender --background cube2.blend --python mainscript.py -- example args 123
```

## Script arguments
In this script the Arguments are called via command line are explained here.

| Argument    | Explanation                                                                                                   |
| ----------- | ------------------------------------------------------------------------------------------------------------- |
| `test`      | no pictures are rendered only file paths are logged                                                           |
| `minimum`   | only first picture for every camera is rendered                                                               |
| `pre`       | renders are in low resolution                                                                                 |
| `test-rend` | renders pictures in human readable file paths<br>- `script-name`<br>  - `layer-1`<br>  - `layer-2`<br>  - ... |

## Script Examples
964_ext called from windows command line
```Terminal
blender -b 964_ext_238.blend -P ../../../../../../../../Desktop/EP_Repo/ansible-server-management/roles/blender_scripting/files/964_ext.py pre min test-rend
```

964_ext: Renders in TEST_MODE: only file paths and file count is logged
```Terminal
blender -b Documents/mass-rend-test/964_ext_206.blend -P Documents/w-s/ansible-server-management/roles/blender_scripting/files/964_ext.py test
```

964_int: Renders in MINIMUM_MODE + PREVIEW_MODE + TEST_REND_MODE: minimum amount of preview pictures are rendered in human readable form
```Terminal
blender -b Documents/mass-rend-test/964_int_173.blend -P Documents/w-s/ansible-server-management/roles/blender_scripting/files/964_int.py min pre test-rend
```

g_ext_early: Renders in MINIMUM_MODE + TEST_REND_MODE: minimum amount of fullhd pictures are rendered in encapsulated folder style
```Terminal
blender -b Documents/mass-rend-test/g_ext_31.blend -P Documents/w-s/ansible-server-management/roles/blender_scripting/files/g_ext_early.py test min
```

