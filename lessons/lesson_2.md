## LESSON 2: LIST & DICTIONARIES

## LISTS

example:
```
drinks = ["beer", "rum", "vodka", "tequila", "whiskey"]
drinks_served = ["vodka", "beer", "beer", "beer", "rum", "beer", "whiskey"]

print("Available drinks: ")
for drink in drinks:
	print(f"  {drink}")

print(f"The 3rd drink served tonight was a {drinks_served[2]}.")
print(f"The last drink served tonight was a {drinks_served[-1]}.")
```

*TBD*


## DICTS

example:
```
# recipes format: [red, yellow, blue, green, iced, aged, blended]
# karm format: [min karm, max karm]

drinks = {
	"Bad Touch": {
		"owner": "none",
		"recipe": [0,2,2,2,1,0,0],
		"karm": [4,4]
	},
	"Hawaiian Skyline": {
		"owner": "SkylineGazer",
		"recipe": [0,9,2,3,1,0,0],
		"karm": [4,4]
	},
	"Rad Roach": {
		"owner": "AKay74u",
		"recipe": [2,0,1,6,0,0,0],
		"karm": [10,10]
	}
}
```

*TBD*