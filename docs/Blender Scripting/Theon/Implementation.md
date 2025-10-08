Pseudocode
```Python
for each layer
	isolate_layer()
	generate_combinations()
	for each cam
		render()
```
## Layer Isolation
Objects that dont interact (cast shadows) with each other should be rendered alone in layers too reduce combination possibilities.
- overlapping should be holdout
- objects that refract lights should be indirect

## Combinations Generation
Every layer is only dependant on specific objects. This has to be set somewhere

## Rendering