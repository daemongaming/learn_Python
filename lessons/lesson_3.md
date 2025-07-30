## LESSON 3: FUNCTIONS & CLASSES

## FUNCTIONS

A `function` is used to separate code into "blocks" that can repeat the same code over and over, simply by calling the function name where you wish to use it -- and without rewriting all that code!

example:
```
def get_starter():
	return "Got some banana bread from work today"
	
def my_first_function(param_1, param_2):
	starter = get_starter()
	sentence = f"{starter}... {param_1} {param_2}."
	return sentence

param_1 = "HELL"
param_2 = "YEAH"
sentence = my_first_function(param_1, param_2)
print(sentence)
```

This code outputs `Got some banana bread from work today... HELL YEAH.` to the console via `print()`.

In fact -- notice that `print()` also has `()` parantheses brackets at the end? That means `print()` is a function, too! The `print()` function is one of many "default" functions built into Python, but you can and will "define" your own functions.

To define a function, type `def ` and then the function name, with the `()` parantheses brackets at the end of the name, and the `:` colon symbol. After that, indent the code you want to run when the function is called.

You can even put variables into these parantheses as `parameters` to be passed into the function, so that the function code can access variables that aren't in its `scope`! 

Notice `param_1` and `param_2` were defined later in the code, but they are "sent" to the function in the parantheses when the function is called, because the definition expects them!

For the `print()` function, the parameter we pass in is a string, because `print()` accepts 1 string as a parameter.

Take note of the `return` statement at the end of our function, which breaks out of the function and "returns" to the code where the function was called, to continue on with the rest of the code.

You can also pass variables back to the code that called the function by putting the variable as a part of the `return` statement, as above in the example code.

Returning a variable makes the function's output essentially equivalent to that variable's value, which is why we can set `sentence` to equal the output of `my_first_function(param_1, param_2)`.

You may find the term `methods` is used interchangeably with `functions`, especially in other programming languages, as they have similar uses. The only difference is that a `method` is a type of function called *inside* the scope of a `class`.

## CLASSES

A `class` is used to separate code into modular chunks, especially in order to keep certain functions & variables contained properly in a scope of its own.

Basically, we just group code together into classes, so that their code doesn't overlap with other classes (or `global`) code, as well as to be able to reference the class's code easily.

Imagine a class as an `object`. We can make as many copies of the object as we want, and they are all the same *type* of object -- but they are totally individual objects of their own!

example:
```
class Person:
	def __init__(self, name, avatar, adjective):
		self.name = name
		self.avatar = avatar
		self.adjective = adjective
	def get_quote(self):
		quotes = {
			"AKay": "Cheeers!",
			"Kraken": "Yo! Salud!",
			"BitchKing": "durrr...",
			"Melty": "Pay me a grand for some pixels!"}
		return quotes.get(self.name)
	def print_person(self):
		print(f"\n{self.name}: {self.avatar} -- the {self.adjective} {self.avatar}!")
		print(f"\"{self.get_quote()}\"")

def print_people(people):
	print("\n=================\n   PEOPLE LIST   \n=================")
	n = 0
	for person in people:
		n += 1
		print(f"Person #{n}: {person.name}")
	print("-----------------")

akay = Person("AKay", "Rad Baddie", "baddest")
kraken = Person("Kraken", "Rad Roach", "raddest")
bk = Person("BitchKing", "Drunken Idiot", "saddest")
jk = Person("Melty", "Bottom", "maddest")

people = [akay, kraken, bk, jk]

def get_choice():
	quits = ["quit", "exit", "stop", "end", "leave", "gtfo"]
	choice = input("> Enter a number: ")
	if choice in quits:
		quit()
	else:
		return choice

def main():
	print_people(people)
	print("\nWelcome to our list of people!\n\nPlease select a person from the list above in order to see their description.")
	choice = get_choice()
	max = len(people)    # gets the length of the list, aka max number choice
	try:
		choice_num = int(choice)
	except Exception:
		pass
	while choice_num not in range(0, max):
		print("\nInput not recognized!\n")
		choice = get_choice()
	person = people[choice_num]
	person.print_person()
    
main()
```

The class `Person` above has several functions defined inside of it, with the first one being `__init__(self)`.

It is good practice to define the `__init__()` function taking the parameter `self` for a class in order to "initialize" certain values that can be used in the scope of the whole class.

The `self` parameter just gets the scope of the class, so we can work with those initialized values -- or even values modified by another function elsewhere in the class!

Note: we do *not* need to pass `self` as a parameter when the function is called, but we *do* need to have it in the function's definition; also, `self` should only be used in a class scope, not "global"!

Notice the `main()` function that is defined, and called, at the bottom of the code.

It is common practice to have a "main" script that acts as a sort of "entry point" for the code to start at.