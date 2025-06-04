This program is not memory safe for different reasons.

- Blender files are loaded and are massive rendering these requires at least 32gb ram or 8gbvram
- Blender Files are not cleane up properly on runtime
- Python generates too many combinations

## Blender Files
Memory usage stays consistent based on different Layers. Each Layer can change the vertex structure which leads to more memory usage
```
Images: 112  
Materials: 152  
Meshes: 581  
Objects: 770  
Node Groups: 112
```

## Blender Cleanup
adding cleanup like cleaning up freed objects doesnt change memory usage

## Python Memory Leaks
Python Memory shows to be consistent
`Total Python objects: 46296`

### Observations
Running in lowpower mode on mac + test mode runs without crashing