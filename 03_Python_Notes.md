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
- inside the folder, create a file named `main.py` or `app.py` (or any name you prefer)
- create a folder named `src` or `lib` to store your source code
- inside the `src` or `lib` folder, create a file named `__init__.py` to make it a package
- create additional modules (Python files) as needed in the `src` or `lib` folder
- if you have multiple modules, you can create subfolders to organize them further
- create a `requirements.txt` file to list the dependencies for your project
- create a `README.md` file to document your project

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

<hr/>

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
