
```Python
RENDER_RESOLUTION_X = 2560
RENDER_RESOLUTION_Y = 1440
RENDER_RESOLUTION_PERCENTAGE = 100

CYLCES_ADAPTIVE_THRESHOLD = 0.025
CYLCES_SAMPLES = 512

# PreRender Settings
PRE_RENDER_RENDER_RESOLTION_PERCENTAGE = 50
PRE_RENDER_CYLCES_ADAPTIVE_THRESHOLD = 0.5
PRE_RENDER_CYLCES_SAMPLES = 1

#If True, the script will only output the paths to the images and count the renderings

# If False, the script will render the images
TEST_MODE = (
False # Nur die Pfade zu den Bildern ausgeben und die Renderings zählen
)
RENDER_MINIMUM = True
MINIMUM_COUNT = 1 # Minimale Anzahl der Renderings
PRE_RENDER = True # Bilder in niedriger Qualität vorrendern
VERSION = "3" # Version der Blocker-Datei
BASE_PATH = (
"./renderings/output/elferplatz/"
if platform.system() == "Darwin"
else "/root/renderings/output/elferplatz/"
)

OUTPUT_TEMPLATE = "./B01/E_Ext/E{999}/M{0}-{1}-{2}/P{3}/FL{4}/V{5}/R{6}/F{7}-{8}-{9}/BS{10}-{11}/SW{12}-{13}/RL{14}/SP{15}/BG{16}/SZ{17}/FW{18}/DS{19}/KZ{20}/AS{21}"
```