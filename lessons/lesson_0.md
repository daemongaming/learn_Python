# LESSON 0: BASIC SYNTAX & VOCAB

## VARIABLES

A container that holds data, with an assigned name. when that name is used in the code, it references the data it is assigned to for use in the code.

example:
```
enabled = False
word = "bird"
number = 1
```

In this example, we set (or "initialize") a variable named `enabled` equal to the boolean value `False`, so that whenever we use `enabled` in the code, it refers to the value `False` -- unless we change it later!

Same with `word` referencing the string `"bird"`, and `number` referencing the integer (number) `1`.

Strings (text), integers (whole numbers), and booleans (True/False) are the three most basic type of variables you will work with. Get used to using them!


## PRINTING

A useful "method" (aka a "function") that lets us "print" (aka "display text") to our current terminal window.

example:
```
word = "FORMATTED"
number = 2

print('This is a regular string to be printed!')
print(f"This is a {word} string, with {number} variables!")
```

The first print method just prints the string out directly. Uses apostrophe quotes.

The second one has an `f` in front of the string's initial quotation mark, inside the parantheses (curved brackets).

This allows us to use curly brackets to insert variables into the text programmatically -- aka "formatting" the string.

protip:
```
Most editors show strings as a certain color, such as green, but if you've remembered to format your string correctly, the editor will show all brackets and the variables inside them as their own white color!
```

## OPERATORS

Can be used to do things with variables, like dividing one integer by another, or combining two strings together.

It's basically math, so be careful when you're doing things like adding boolean values -- remember that booleans `False` and `True` are equivalent to `0` and `1`! `False + True` equals `True`, but `False * True` equals `False`. Get it?

example (w/ integers):
```
magic = 42       # `magic` becomes equivalent to `42` (assignment)

magic + magic    # equivalent to `84` (addition)
magic - magic    # equivalent to `0` (subtraction)
magic / magic    # equivalent to `1` (division)
magic * magic    # equivalent to `1764` (multiplication)

magic > magic    # equivalent to `False` ('greater than' comparison)
magic >= magic   # equivalent to `True` ('greater than or equal to' comparison)
magic != magic   # equivalent to `False` ('not equal to' comparison)
```

example (w/ strings):
```
word = "bird "
phrase = "is the word"

sentence = word + phrase    
	# `sentence` becomes equivalent to 
		`"bird is the word"`
sentence = sentence + " b-b-" + word + word + word + "!" 
	# `sentence` becomes equivalent to 
		`"bird is the word b-b-bird bird bird!"`
```

example (w/ booleans):
```
True == True     # equivalent to `True` ('equal to' comparison)
True == False    # equivalent to `False` ('equal to' comparison)
True != True     # equivalent to `False` ('not equal to' comparison)
True != False    # equivalent to `True` ('not equal to' comparison)
```