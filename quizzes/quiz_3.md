# QUIZ[3]

1. What do we call the variables that we "pass into" functions?

2. What is the name of the function that should always be defined when creating a class?

3. [TRICKY Q!] What is the output of the following code block, and why did it pick one version of that variable over the other?

```
phrase = "HELL YEAH"

class Clanka:
	def __init__(self, phrase):
		self.phrase = "HELL NO"
	def speak(self):
		print(f"{phrase}!")
		
clanka = Clanka("HELL NO")
clanka.speak()
```

4. Write a simple `function` definition that takes in 3 string parameters and prints all 3 parameters out when called. Make all 3 parameters the name of a Mid Bar drink.

5. Write a simple `class` that has (defines) `__init__(self)` and `add(num_1, num_2)` functions. The `add()` function should add `num_1` and `num_2` together and `print()` the result when called. Set `num_1` to the number in your username, and set `num_2` to `346`.