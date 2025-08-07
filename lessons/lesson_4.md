## LESSON 4: MODULES & DEPENDENCIES

## IMPORTS & DEPENDENCIES

When a program needs to interact with, or "hook" into, another program's code in order to use its various functions and values, we call that a *dependency* -- the one program is dependent on the other.

In Python, we can `import` the code from other scripts in order to use it. Usually we do this at the top of the script (global scope), before anything else is defined or called, but you may see it used in other scopes as well.

Here are some of the ways we can import code:
1. To import a default module, such as `sys` or `os`, we can simply type `import <module_name>`.
2. To import a custom script, we just use `import <file_name>`, without the file type `.py` at the end.
3. To import a specific part of a module or custom script, we can use `from <module_name> import <class_name>`.
4. To import a module and assign it a name to reference, we can use `import <module_name> as <reference_name>`.

example:
```
import sys
import os

from my_first_module import my_first_function, my_second_function

from my_first_module import (
	Class1, Class2, Class3
)

import my_first_subdir/my_second_module as mod_2
```

For this example, we first import the default modules `sys` and `os`, which are commonly imported to perform all sorts of basics functions, such as accessing files on the local machine.

Next, we use `from` to import specific methods/functions in one line; below that, we use multiple lines to achieve something similar to import the various classes from the module.

Finally, at the bottom, we import a module from a custom script located in a sub-directory (i.e., a folder) inside of the project's "root" directory (or the "top" level folder that has the other folders inside), and assign it a reference name `mod_2` to it.

These various methods can be used mostly interchangeably to import modules/scripts into your program at `runtime`.

***WARNING!*** Avoid "circular" imports! If `script_1.py` imports `script_2`, but `script_2.py` also imports `script_1`, well... you're gonna have a bad time!


## MODULES

We can split our project's code into multiple scripts, each their own `module` -- and indeed all projects that aren't one-offs should probably implement this practice.

This "splitting" of code between multiple scripts is called "modularity", and it allows us to keep our codebase organized and easy to read.

Below are two separate scripts in the same directory, or folder.

example `my_first_module.py`:
```
class Class1:
	def __init__(self, phrase):
		self.phrase = phrase
	def get_output(self):
		return self.phrase

class Class2:
	def get_output(self):
		return "F**KIN' COPS? HELL. NO."
		
class Class3:
	def get_result(self, num):
		return (num * num)
	
def my_first_function(starter, param_1, param_2):
	sentence = f"{starter}... {param_1} {param_2}."
	return sentence
	
def my_second_function(phrase):
	sentence = f"{phrase}"
	return sentence
```

example `my_first_script.py`:
```
import sys
import os

from my_first_module import (
	Class1, Class2, Class3, my_first_function, my_second_function
)

class_1_obj = Class1("Got some banana bread from work today")
output_1 = class_1_obj.get_output()

class_2_obj = Class2()
output_2 = class_2_obj.get_output()

class_3_obj = Class3()
output_3_a = class_3_obj.get_result(20) + 20
output_3_b = class_3_obj.get_result(8) + 5

sentences = [
	my_first_function(output_1, "HELL", "YEAH"),
	my_second_function(output_2),
	f"{output_3_a}{output_3_b} smoke erry day!"
]

for sentence in sentences:
	print(sentence)
```

Notice that in the `my_first_module` script, we only define classes and functions, but don't call anything; this is because they are called in `my_first_script`, after they are imported.

Once they are imported, we can use them just like we would any other function/class in our script, simply by calling them by their reference name, like so: `import my_first_module`, followed by `class_1_obj = Class1()` and so forth.