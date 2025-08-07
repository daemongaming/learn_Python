# QUIZ[4]

> Assume you are making a Python program, which will have a `dependency` on a `module` named `pyopengl`.

1. Write 1 line of code that adds the `pyopengl` dependency to your script.

2. Write 1 line of code that imports `sys`, `os`, and `json` altogether.

3. Write 1 line of code that imports a script named `painter.py` as the name `artist`.

4. Write 1 line of code that imports a script named `menu_widget.py` from the project sub-directory `widgets`.

5. Write a script that does not create any new variables, but still outputs the number `42`, considering the following script named `question.py` is also in your project's "root" directory:

```
class Answer:
	def __init__(self, magic_num):
		self.magic_num = magic_num
	def get(self, bonus):
		return self.magic_num + bonus
		
def get_answer(bonus):
	answer = Answer(40)
	return answer.get(bonus)
```