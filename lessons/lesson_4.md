## LESSON 4: MODULES & DEPENDENCIES

## IMPORTS & DEPENDENCIES

example:
```
import sys
import os

from my_first_module import my_first_function, my_second_function

from my_first_module import (
	Class1, Class2, Class3
)
```

*TBD*


## MODULES

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
# using the same imports from the Imports & Dependencies section above:

class_1_obj = Class1("Got some banana bread from work today")
output_1 = class_1_obj.get_output()

class_2_obj = Class2()
output_2 = class_2_obj.get_output()

class_3_obj = Class3()
output_3_a = class_3_obj.get_result(8) + 5
output_3_b = class_3_obj.get_result(20) + 20

sentences = [
	my_first_function(output_1, "HELL", "YEAH"),
	my_second_function(output_2),
	f"{output_3_a}{output_3_b} smoke erry day!"
]

for sentence in sentences:
	print(sentence)
```


*TBD*