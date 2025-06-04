should always be in test mode when called from blender. Uses environment var for turning test mode off

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

| Argument  | Explanation                                         |
| --------- | --------------------------------------------------- |
| `test`    | no pictures are rendered only file paths are logged |
| `minimum` | only first picture for every camera is rendered     |
| `pre`     | renders are in low resolution                       |
