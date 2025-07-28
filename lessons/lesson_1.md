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
for i = 0; i < 10; i++: 
	num = i + 1
	print(f"This is line {num}")
```

*TBD*


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

*TBD*