# Helpers
Files that are universally used and hold the main code and configurations for the Blender file

### Cloud Config
Contains Cloud Configurations. As this Documentation is public im not talking about the content see for yourself!

### Cloud Helpers
Contains functions to interact with the cloud.

| `upload_to_s3(file_path)` | 
| ---------------- | 
| Uploads file in file_path to the cloud. File path on the cloud is the same as file_path| 

| `create_lockfile(file_path)` | 
| ---------------- | 
| Creates a Lockfile that prevents multiple servers rendering the same image| 

| `check_if_lockfile_exists(file_path)` | 
| ---------------- | 
| Looks up the Lockfile that prevents multiple servers rendering the same image| 

### Render Settings
Uses system Args to set different Render flags. All Flags are explained here: [Using command line Arguments](../Headless%20Rendering/Using%20command%20line%20arguments.md)

| `set_render_settings()` | 
| ---------------- | 
| Sets the Rendering Engine for Optix, Darwin based systems. Sets Blender render settings to Cycles, Resolution and Samples based on input. See more at [Render Settings](Render%20Settings.md) | 

### Shared Colors
Contains colors used by all Cars.

### Shared Helpers
Heart of the code.

| `generate_combinations(configuration)` | 
| ---------------- | 
| Return Cartesian product (Set x Set) of configuration key sets. This generates all possible combinations out of the Sets. configurations: list of (path, mapping_dict) pairs; uses mapping_dict.keys()| 

| `check_exceptions(config, slot_mapping=None)` | 
| ---------------- | 
| Validates a combination against model/bodykit constraints. Returns False to skip rendering if forbidden pair occurs. slot_mapping: name -> index; only checks when both 'model' and 'bodykit' exist. |

| `create_output_path(template, layer, configurations, slot_mapping, combination, path_pattern)` | 
| ---------------- | 
| Resolve OUTPUT_TEMPLATE placeholders and drop empty identifier blocks. Fills {layer} and feature placeholders using mapping dicts from configurations, filters segments matching identifier tokens with all X values, and prefixes BASE_PATH. |

| `georefresh(objects)` | 
| ---------------- | 
| Force a Blender refresh on listed objects by toggling modifier viewport state. |

| `reset_scene(active_loop)` | 
| ---------------- | 
| Reset scene modifiers and default color values before each render loop. Keeps specific settings for special loops to avoid unintended overrides. |

| `set_camera(camera_name)` | 
| ---------------- | 
| Set the active camera to the object named camera_name if it exists. |

| `switch_light_setups(camera_name, light_setups)` | 
| ---------------- | 
| Apply a predefined light rig index for the given camera name if mapped. |

| `switch_glass_setups(camera_name, glass_setups)` | 
| ---------------- | 
| Set compositor glass variant index based on camera name mapping. |

| `felgenlicht(camera_name)` | 
| ---------------- | 
| Toggle special rim lights on certain cameras |

| `render_scene_with_config()` | 
| ---------------- | 
| This is the main function that renders all possible combinations of configurations. Understanding this is the main task of the code. |
Renders all combinations across cameras, writing outputs per template. Writes Blender sockets from config via `exec(f"{path} = {key}")`, refreshes Blender, switches lights/glass per camera, and renders and uploads. |
To test this function use system arg `test`. This prints logs instead of rendering.|
To test the renderings use `min` to only render the first combination. Use `pre` for a preview, low resolution and samples. Use `test-rend` to make the output path human readable |

| `print_output_logs()` | 
| ---------------- | 
| Summarize TEST_MODE results: per-loop counts, per-layer counts, duplicates, totals. 
Important are duplicates if they appear an image will be rendered twice overwriting itself. This mostly happens if two keys have the same name leading to invisible parts in the final frontend image |

| `render_loops()` | 
| ---------------- | 
| Execute selected render loops with distributed locking across hosts. On render servers, staggers startup, creates/reads lockfiles, runs functions, and reloads the .blend between loops to reset state. When not the owner, optionally re-enters in helper mode to assist ongoing loops. |