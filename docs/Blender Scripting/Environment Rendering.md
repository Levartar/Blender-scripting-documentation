- Background should contain detailed 3D scene
- Background should be interchangeable
- Only 1 Camera perspective


## Implementation
- LInk Environemts into 964_ext.blend file
- Geometry node switch for different environments 
- Compositor for Environment on new Scene layer 
- 5 Cameras for different sweet spot photos
- setup car rotation based on different sweet spot cameras 
	- `[Cam1: 0°, Cam2: 45°...]`

- Code create new CFS for environment Geometry node switch
- Create render environment sister function (called out of main render function)

```PYthon
# Environment

def Environment():

bpy.data.objects["Car_Instancer_Base"].modifiers["GeometryNodes"]["Socket_4"] = 0

configurations = [
CFS["Bodykits"],
CFS["FelgenFull"],
CFS["Distanzscheiben"],
CFS["Distanzscheiben"],
CFS["BGColorComp"],
]

  

slot_mapping = {

"bodykit": 0, # Bodykits

"felge": 1, # FelgenFull

"distanzscheibeV": 2, # Distanzscheiben

"distanzscheibeH": 2, # Distanzscheiben

"hintergrund": 3, # CompositorHintergrund

}

  

render_scene_with_config(

"Hintergrund",

cameras["CamsBG"],

"Hintergrund",

configurations,

slot_mapping,

"E0",

OUTPUT_TEMPLATE,

path_pattern,

georefreshObjects,

light_setups,

)


configurations = [
CFS["Bodykits"],
CFS["FelgenFull"],
CFS["Distanzscheiben"],
CFS["Distanzscheiben"],
CFS["Environment"],
]

render_scene_with_environment( 

"Environment",

cameras["EnvCam"], #has camera car rotation switch

"Environment",

configurations,

slot_mapping,

"E0",

OUTPUT_TEMPLATE,

path_pattern,

georefreshObjects,
)
```

