## LESSON 2: LIST & DICTIONARIES

## LISTS

A list allows us to store values, in order.

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

The list `drinks` contains values inside square brackets `[]`, with each value separated by a comma.

That value can be used later by referencing the list's name and the `index`, a number indicating its order in the list.

If you want the first item in the `drinks` list, you would use `drinks[0]`. You can also work backwards, getting the last item with `drinks[-1]`.


## DICTS

A dictionary object allows us to store a lot of organized information.

example:
```
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

We can use a dictionary to store values with a specific ID, which we can then reference to recall that value later with `.get()`.

For instance, to get the `owner` name of a drink named `Bad Touch`, you would use `drinks.get("Bad Touch")`.

To get the second value in the `recipe` list of the `Hawaiian Skyline`, you would use `drinks.get("Hawaiian Skyline")[1]`.