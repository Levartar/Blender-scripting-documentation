We are generating Configuration by multiplying dictionaries to get all possible Combinations

```Python
def generate_combinations(configurations):
	values = [list(config[1].keys()) for config in configurations]
	return list(itertools.product(*values))
```

Configurations are dicts like:
```Python
Models = {
	1: "02", # Cabrio
	2: "03", # Targa
	3: "04", # Turbo
	0: "01", # Coupe
}

HexUnilack = { #Color
	"#FCFCFC": "U02",
	"#CFC7B5": "U03",
	"#18253C": "U04",
	"#253E8F": "U05",
	"#096899": "U06",
	...
}

Decals = {
	0: "01", # Carrera
	1: "02", # Porsche Line
}

Kennzeichen = {
	0: "00", # Ohne
	1: "01", # Deutschland
	2: "02", # Österreich
	3: "03", # Schweiz
}
```