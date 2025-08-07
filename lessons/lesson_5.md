## LESSON 5: JSON & FILE HANDLING

## FILE HANDLING

Sometimes we need to access other files, most commonly in order to access data stored in a particular text format, such as JSON.

We store data in separate files to increase modularity, meaning we can edit them on the fly without needing to edit the actual code, either manually or programmatically.

A good way to tell if you should be modularizing a particular value (or more likely, a set of values like a list or dict) is if you're using it in more than one scope.

Don't repeat yourself in your scripts, otherwise to change one value you will need to also change all other versions of it in all of your scripts! This mistake is called "hardcoding" and it is unsustainable.

In the example below, we have a script with a function that takes in a string `file_name` and returns a `json` object, which can then be used just like a dict to get our data.

example `load_json.py`:
```
def load_file(file_name):
    file_path = get_resource_path(file_name)
    if os.path.exists(file_path):
        with open(file_path, "r", encoding="utf-8") as f:
            return json.load(f)
    else:
        raise RuntimeError("Error! File not found!")

FILE = load_file("drinks.json")
```

There are many types of files that can be accessed, ranging from media files (images, video, audio, etc.) to binary files (raw "serialized" data in 0s and 1s that can be "decoded" or "deserialized").

Each different file type may come with its own unique "proper" methodologies for accessing and utilizing the data within, but it is sufficient for most use-cases to simply know how to work with text files, especially of the type `.json`.


## JSON FILES

A JSON file holds data, usually in a dictionary format, and can be accessed in much the same way once the JSON object is loaded using `import json`.

Below is a familiar example, which should indeed remind you of a dict:

example `drinks.json`:
```
{
    "B-T3ND3R": {
        "owner": "Mr-Bartender",
        "recipe": [0,2,0,0,1,0,0],
        "karm": [0,18]
    },
    "Bad Touch": {
        "owner": "None",
        "recipe": [0,0,0,0,1,0,0],
        "karm": [4,4]
    },
	"Rad Roach": {
        "owner": "AKay74u",
        "recipe": [2,0,1,6,0,0,0],
        "karm": [10,10]
    },
	"Sugar Rush": {
        "owner": "None",
        "recipe": [2,0,1,0,0,0,0],
        "karm": [0,17]
    }
}
```

Notice that we are "nesting" dictionaries inside of a dictionary here? Using both examples above together, we can get the entire `Rad Roach` dictionary with `rad_roach = FILE.get("Rad Roach")`, and then we can get each value with `rad_roach.get(val)`, where `val` is a key string like `owner` or `karm`.