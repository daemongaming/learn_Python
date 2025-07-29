## LESSON 1: CONDITIONALS & LOOPS

## IF-ELSE

aka "conditionals", because they check if a certain condition is met -- in this case if a statement is true -- and "branches" to the proper indented "block" of code accordingly.

example:
```
enabled = False
word = "bird"

if enabled:
	print("Enabled!")
elif enabled and word != "bird":
	print("Bird is NOT the word.")
elif not enabled and word == "bird":
	print("Bird is the word.")
else:
	print("Not enabled!")
```

Since `enabled` is initially set to `False`, aka not `True`, the first block of code under the `if enabled:` section is not activated.

Then it checks the next one in order, until it reaches a condition that is met successfully.

In this example, the third block is executed (aka "run") because the condition of "not enabled" (aka that enabled is set to False) is met, as well as the condition that "word is equal to the string 'bird'".

If the `if` condition, as well as any `elif` (aka "else-if") conditions, are not met, then it defaults to the `else` condition at the end.

If there is no `else` condition, and none of the other conditions are met, then no code is executed for that if-else block.


## FOR LOOPS

example:
```
for i in range(0,10): 
	num = i + 1
	print(f"This is line {num}")
```

This prints out "This is line 1" then a new line, and "This is line 2", and so on to line 10.

The `range(0,10)` counts from the first number (inclusive) and stops before the last number (exclusive). So, this one starts at `0` and then stops at `9`.


## WHILE LOOPS

example:
```
done = False    # our 'flag' variable, which kicks us out of the loop when set to `True`
count = 0

while not done:
	if count < 10:
		print(f"This is line {num}")
	else:
		done = True
```

This loop does the same thing as the `for` loop above, manually counting up through each loop! :)