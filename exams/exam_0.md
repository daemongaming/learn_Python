# EXAM 0 - APPRENTICE LEVEL - BASICS OF SCRIPTING

***Write a script that contains the following items:***

- a `list` named `owners_data`, containing at least 7 *MidBar* drink owners (*remember: `_list = [...]`*)

- a `dict` named `drinks_data`, containing at least 7 *MidBar* drinks entries (*remember: `_dict = {...}`*)
  - each entry into the `drinks_data` dict should having the follow items:
    - Key: an uppercase version of the name string
    - Values (as a nested dict): 
	  - `name`: a string for the name of the drink, in plain text
	  - `owner`: a string for the name of the drink owner, in plain text
	  - `recipe`: an integer list containing 7 values, for the drink ingredients
	  - `karm`: an integer list containing 2 values, for the min/max karm levels

- a `class` named `Drink` that is used to create a `list` of drink objects from the drinks data (*remember: `class Class` & `_class = Class()`*)
  - the class should create `Drink` objects that have the following items:
    - defines an `__init__()` method that performs the following functions:
	  - takes in the parameters `self` and `_data` (an entry in `drinks_data` dict)
	  - sets each value in `_data` to `self` (*e.g., `self._name = _data.get('name')`, etc.`*)
	- defines a `karm_roulette()` method that performs the following functions:
	  - takes in the parameters `self`
	  - returns a value between the two values in the `self._karm` list (*remember that `range(a,b)` starts at `a` and ends right before `b`!*)

- a `function` named `main()` that is called at the end of the script to start the program, that performs the following function:
  - creates & initializes the `owners_data` & `drinks_data` variables inside the `main()` function scope (*i.e., NOT global!*)
  - creates a list of `Drink`-class objects named `drinks` by looping through each entry in `drinks_data`
  - prints all drink owners by looping through each value in `owners_data`
  - prints all drink names by looping through each entry in `drinks_data` for its `self._name` value
  - allows the user to input a drink name to get the info for that `Drink` object
    - uses the input to get the matching object from `drinks`
	- prints each value for that drink entry
  - finally, calls `quit()` to end the program