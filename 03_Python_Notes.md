**Difference between function and method**

- Functions which are defined inside a class are called methods. Functions which are defined outside a class are called functions.

- **Function**: A block of reusable code that performs a specific task. It can be defined using the `def` keyword and can be called independently. Functions can take parameters and return values.
- **Method**: A function that is associated with an object or class. Methods are defined within a class and are called on instances of that class. They can access and modify the object's state and are defined using the same `def` keyword. Methods are typically used to operate on the data contained within the object.

**How to install virtual environment in python**

- common way: using `venv` (traditional way)

```bash
python3 -m venv <name_of_your_env>
```

- activate the environment

```bash
source <name_of_your_env>/bin/activate
```

- deactivate the environment

```bash
deactivate
```

<br />

for activation of virtual environment in **windows**

```bash
<name_of_your_env>\Scripts\activate
```

<br />

installing packages in virtual environment

```bash
pip install <package_name>
```

installing packages in virtual environment from requirements.txt

```bash
pip install -r requirements.txt
```

requirements.txt file is a text file that contains a list of packages to be installed using pip.

the name of the file is `requirements.txt` by convention, but you can name it anything you want.
<br />
To install specific version of a package, you can specify the version number in the requirements.txt file like this:

```
package_name==1.0.0
```

<hr />

New way to create virtual environment is `uv`

<hr />

**How to organize your python code**

- create a folder for your project

<hr />

**Difference between modules and packages in python**

- **Module**: A single file containing Python code, which can define functions, classes, and variables. It can also include runnable code. Modules are imported using the `import` statement.
- **Package**: A directory that contains multiple modules and a special `__init__.py` file. The `__init__.py` file can be empty or execute the initialization code for the package. Packages allow for a hierarchical organization of modules, enabling a structured way to group related modules. Packages are also imported using the `import` statement, but they can include sub-packages and modules.

<hr />

**Object and mutability**

- **Object**: In Python, everything is an object. An object is an instance of a class and can have attributes (data) and methods (functions). Objects can be mutable or immutable.

Object have identity, type, and value.

For immutability, the object cannot be changed after it is created. For example, strings and tuples are immutable objects in Python.
**To checking the mutability of an object**, you can use the `id()` function to get the identity of the object and compare it before and after an operation that is supposed to change the object.

But never use `id()` to check mutability in production code, as it is not a reliable method for checking mutability. Instead, you should know the type of the object and its mutability characteristics.

Never use value comparison to check mutability, as it can lead to unexpected results. Instead, use the type or identity of the object to determine its mutability.

```python
a = [1, 2, 3]
print(id(a))  # Get the identity of the object
a.append(4)  # Modify the object
print(id(a))  # Check the identity again
```

If the identity remains the same, the object is mutable. If it changes, the object is immutable.

In simple terms **immutability** means that once an object is created, it cannot be changed. For example, strings and tuples are immutable in Python, meaning you cannot modify their content after they are created. Lists and dictionaries, on the other hand, are mutable, allowing you to change their content.

each immutable object has its own identity, which is a unique identifier for that object in memory. When you create a new immutable object, it gets a new identity, even if its value is the same as an existing object.

```python
sugar_amount = 2
print(f"Initial sugar: {sugar_amount}") #2
sugar_amount = 12
print(f"Second Initial sugar: {sugar_amount}") #12
print(f"ID of 2: {id(2)}") #140737488346112
print(f"ID of 12: {id(12)}") #140737488346144
```

In this example, the identity of the integer objects 2 and 12 is different, even though they are both integers. This shows that immutable objects have their own identity.

<hr />

**Numbers**

- **int**: Integer type, used for whole numbers (e.g., 1, 2, -3).
- **float**: Real number(Floating-point type), used for decimal numbers (e.g., 1.5, -2.3).
- **complex**: Complex number type, used for numbers with a real and imaginary part (e.g., 1 + 2j).
- **bool**: Boolean type, used for True/False values (e.g., True, False).

The division operator `/` always returns a float, even if the result is a whole number. If you want to perform integer division (floor division), use the `//` operator.

```python
a = 5
b = 2
print(a / b)  # Output: 2.5 (float division)
print(a // b)  # Output: 2 (integer division)
```

In python, the types which can be converted to `False` are:

```python
False, None, 0, 0.0, 0j, [], (), {},
set(), '', b'', bytearray(), memoryview(b'')
```

Other than these types, everything else is considered True.

- the `b` here is used to denote a byte string, which is a sequence of bytes. It is often used for binary data or when working with files in binary mode.

**Logical Operators in Python**

- **and**: Returns True if both operands are True.
- **or**: Returns True if at least one operand is True.
- **not**: Returns True if the operand is False, and vice versa.

**Strings**

Strings are immutable sequences of characters. They can be defined using single quotes, double quotes, or triple quotes for multi-line strings.

In Python, when slicing strings using the `[]` operator, the end index is not inclusive—meaning the character at the end index is not included in the result. This behavior is also the same in JavaScript when using the `slice()` method: the substring returned includes the character at the start index but excludes the character at the end index.

**Example in Python:**

```python
s = "hello"
print(s[1:4])  # Output: 'ell'
```

**Example in JavaScript:**

```javascript
let s = "hello";
console.log(s.slice(1, 4)); // Output: 'ell'
```

there is also third parameter in slicing which is the step size. It allows you to skip characters in the string.

```python
s= "hello"
print(s[0:5:2])  # Output: 'hlo'
```

the first parameter and second parameter are the start and end indices, and the third parameter is the step size.

first and second parameter are also optional, if you don't provide them, it will take the whole string.

```python
s = "hello"
print(s[::2])  # Output: 'hlo' (every second character)
print(s[::-1])  # Output: 'olleh' (reversed string)
```

**Membership**

- **in**: Checks if a substring exists within a string.
- **not in**: Checks if a substring does not exist within a string.

```python
s = "hello"
print("e" in s)  # Output: True
print("x" not in s)  # Output: True
```

<br />
<br />

**Tuples**

- A tuple is an ordered collection of items that can contain elements of different types, including other tuples. Tuples are immutable, meaning you cannot change their content after creation. They are defined using parentheses `()`, and elements are separated by commas.
- Tuples can be indexed and sliced, similar to lists, but they cannot be modified after creation.

```python
my_tuple = (1, 2, 3, "hello", (4, 5))
print(my_tuple[0])  # Output: 1
print(my_tuple[3])  # Output: 'hello'
print(my_tuple[4][1])  # Output: 5 (accessing an element from a nested tuple)
```

Tuples are often used to group related data together, and they can be _unpacked_ into variables:

```python
x, y, z = (1, 2, 3)
print(x)  # Output: 1
print(y)  # Output: 2
print(z)  # Output: 3
```

Tuples can also be used as keys in **dictionaries** because they are immutable, while lists cannot be used as dictionary keys.

```python
my_dict = {(1, 2): "value1", (3, 4): "value2"}
print(my_dict[(1, 2)])  # Output: 'value1
```

Tuples are generally used when you want to ensure that the data cannot be modified, or when you want to use them as keys in dictionaries. They are also slightly more memory-efficient than lists due to their immutability.
<br />

<hr/>

**List** _(mutable data type)_

- A list is an ordered collection of items that can contain elements of different types, including other lists. Lists are mutable, meaning you can change their content after creation. Similar like arrays in other programming languages, lists can be indexed and sliced.
- Lists are defined using square brackets `[]`, and elements are separated by commas.

```python
my_list = [1, 2, 3, "hello", [4, 5]]
print(my_list[0])  # Output: 1
print(my_list[3])  # Output: 'hello'
print(my_list[4][1])  # Output: 5 (accessing an element from a nested list)
```

**Set** _(mutable data type)_

- A set is an unordered collection of unique items. Sets are mutable, meaning you can add or remove elements after creation. They are defined using curly braces `{}` or the `set()` constructor.
- Sets do not allow duplicate elements, and they are useful for membership testing and removing duplicates from a list.

```python
my_set = {1, 2, 3, "hello"}
print(my_set)  # Output: {1, 2, 3, 'hello'}
my_set.add(4)  # Adding an element
print(my_set)  # Output: {1, 2, 3, 'hello', 4}
my_set.remove(2)  # Removing an element
print(my_set)  # Output: {1, 3, 'hello', 4}
```

- Sets do not support indexing or slicing, as they are unordered collections. However, you can check for membership using the `in` keyword.

```python
my_set = {1, 2, 3, "hello"}
print(2 in my_set)  # Output: True
print("world" in my_set)  # Output: False
```

- Sets are often used for operations like union, intersection, and difference, which are common in mathematical set theory.
- Sets can also be used to remove duplicates from a list by converting the list to a set and then back to a list.

```python
my_list = [1, 2, 2, 3, "hello", "hello"]
my_set = set(my_list)  # Convert list to set to remove duplicates
print(my_set)  # Output: {1, 2, 3, 'hello'}
my_list_no_duplicates = list(my_set)  # Convert set back to list
print(my_list_no_duplicates)  # Output: [1, 2, 3, 'hello']
```

**frozenset** _(immutable data type)_

- A `frozenset` is an immutable version of a set. It is an unordered collection of unique items, but unlike a regular set, you cannot add or remove elements after creation. Frozensets are defined using the `frozenset()` constructor.
- Frozensets are useful when you need a set-like structure that should not change, such as when using sets as keys in dictionaries or elements in other sets.

```python
my_frozenset = frozenset([1, 2, 3, "hello"])
print(my_frozenset)  # Output: frozenset({1, 2, 3, 'hello'})
# my_frozenset.add(4)  # This will raise an AttributeError because frozensets are immutable
```

- You can perform set operations like union, intersection, and difference with frozensets, just like with regular sets, but you cannot modify the frozenset itself.

```python
set1 = frozenset([1, 2, 3])
set2 = frozenset([3, 4, 5])
print(set1.union(set2))  # Output: frozenset({1, 2, 3, 4, 5})
print(set1.intersection(set2))  # Output: frozenset({3})
print(set1.difference(set2))  # Output: frozenset({1, 2})
```

- Frozensets can be used as keys in dictionaries or elements in other sets because they are immutable, while regular sets cannot be used in these contexts.

```python
my_dict = {frozenset([1, 2]): "value1", frozenset([3, 4]): "value2"}
print(my_dict[frozenset([1, 2])])  # Output: 'value1'
```

**NOTE** : Dictionaries also have union, intersection, and difference operations, but they are not as commonly used as in sets. Dictionaries are primarily used for key-value pairs, while sets and frozensets are used for unique collections of items.

**Dictionary** _(mutable data type)_

- A dictionary is an unordered collection of key-value pairs. Each key is unique, and it maps to a specific value. Dictionaries are mutable, meaning you can change their content after creation. They are defined using curly braces `{}` with key-value pairs separated by colons `:`.

```python
my_dict = {
    "name": "Alice",
    "age": 30,
    "city": "New York",
    "hobbies": ["reading", "traveling"]
}
print(my_dict["name"])  # Output: 'Alice'
print(my_dict["age"])  # Output: 30
print(my_dict["hobbies"][0])  # Output: 'reading' (accessing a list within a dictionary)
```

Dictionaries can be used to store related data in a structured way, allowing you to access values using their corresponding keys. You can add, remove, or modify key-value pairs in a dictionary.

```python
my_dict["country"] = "USA"  # Adding a new key-value pair
print(my_dict)  # Output: {'name': 'Alice', 'age': 30, 'city': 'New York', 'hobbies': ['reading', 'traveling'], 'country': 'USA'}
my_dict["age"] = 31  # Modifying an existing key-value pair
print(my_dict)  # Output: {'name': 'Alice', 'age': 31, 'city': 'New York', 'hobbies': ['reading', 'traveling'], 'country': 'USA'}
del my_dict["city"]  # Removing a key-value pair
print(my_dict)  # Output: {'name': 'Alice', 'age': 31, 'hobbies': ['reading', 'traveling'], 'country': 'USA'}
```

Dictionaries can also be nested, meaning you can have dictionaries within dictionaries, or dictionaries containing lists or other data structures.

```python
nested_dict = {
    "person": {
        "name": "Bob",
        "age": 25
    },
    "skills": ["Python", "JavaScript"]
}
print(nested_dict["person"]["name"])  # Output: 'Bob'
print(nested_dict["skills"][1])  # Output: 'JavaScript'
```

Dictionaries are widely used in Python for various purposes, such as storing configuration settings, representing JSON data, and managing key-value pairs in applications. They provide efficient access to values based on their keys, making them a powerful data structure for many programming tasks.

<hr />

**After learning python**

- [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
  - 4 spaces, never tabs
  - meaningful variable names
  - use `snake_case` for variable and function names
  - use `CamelCase` for class names
  - use `UPPERCASE` for constants
  - formatters like `black` and `isort` can help maintain code style
- [PEP 20 – The Zen of Python](https://peps.python.org/pep-0020/)

  - Readability counts
  - Simple is better than complex
  - Explicit is better than implicit
  - There should be one-- and preferably only one --obvious way to do it
  - Errors should never pass silently
  - In the face of ambiguity, refuse the temptation to guess
  - Namespaces are one honking great idea -- let's do more of those!
  - In terminal, enter python3 and type `import this` to see the Zen of Python

- [PEP 484 – Type Hints](https://peps.python.org/pep-0484/)
  - Type hints are optional annotations that can be added to function signatures to indicate the expected types of parameters and return values.
  - They help with code readability and can be checked using static type checkers like `mypy`.
  - Example:

```python
def add(a: int, b: int) -> int:
    return a + b
```
