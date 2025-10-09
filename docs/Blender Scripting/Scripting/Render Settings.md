# Render Settings
!This Article is a Stump

The render settings are set when running the script. Resolution and Samples can be set via system arguments but are commonly taken from here. The Blender file is made for Cycles.

```Python
RENDER_RESOLUTION_X = 1920
RENDER_RESOLUTION_Y = 1080
RENDER_RESOLUTION_PERCENTAGE = 100

CYLCES_ADAPTIVE_THRESHOLD = 0.025
CYLCES_SAMPLES = 512

# PreRender Settings
if "pre" in sys.argv:
    PRE_RENDER = True
    RENDER_RESOLUTION_X = 640
    RENDER_RESOLUTION_Y = 360
    CYLCES_ADAPTIVE_THRESHOLD = 0.5
    CYLCES_SAMPLES = 1

VERSION = "3" # Version der Blocker-Datei

# Blender Specific Settings
scene.cycles.device = 'GPU'
scene.render.engine = "CYCLES"
scene.render.image_settings.file_format = "PNG"
```