# QUIZ[5]

1. Use `get_resource_path()` to assign a file path to a variable `fp` using a file named `owners.json`.

2. Write 1 line of code that reads a file at path `fp` and assigns it to a variable `OWNERS_FILE`.

3. Write 1 `if-else` conditional branch that uses `raise RuntimeError("Error! File not found!")` if a file does *not* exist at the path `fp`.

4. Write 1 `with` statement that reads the file at path `fp` as `file` and returns `json.load(file)`.

5. Write a simple script that combines all of the answers above, and define a function `get_owner(name)` that returns any value from the `OWNERS_FILE` in the nested dictionary at key `name`.