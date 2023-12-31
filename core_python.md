## Function

- A function in Python is a reusable block of code that performs a specific task. 
- It allows you to break down your code into smaller, manageable pieces, which makes your code more organized, modular, and easier to maintain.
  
- In Python, a function is defined using the def keyword followed by the function name, a pair of parentheses (), and a colon :. The body of the function is indented and contains the code that gets executed when the function is called.

```python
def my_function():
    # Function body
    print("Hello, World!")

# Calling the function
my_function()
```

- Functions can take input values, called parameters, which are passed within the parentheses during function definition. 
- Parameters allow you to customize the behavior of a function for different inputs.

```python
def greet(name):  # ==> name is parameter here
    print("Hello, " + name + "!")

greet("Alice")  # Output: Hello, Alice!
greet("Bob")    # Output: Hello, Bob!
```

- In Python, when you pass an argument to a function, you're actually passing a reference to the object that the argument points to, rather than the actual value. 
- This means that changes made to the object inside the function can affect the original object outside the function.

```python
def modify_list(lst):
    lst.append(4)
    lst = [10, 20, 30]

my_list = [1, 2, 3]
modify_list(my_list)
print(my_list)  # Output: [1, 2, 3, 4]
```

- Functions can return values using the return statement. When a function is called, the return statement sends a value back to the caller.

```python
def add(a, b):
    return a + b

result = add(3, 5)  # result will be 8
```

## Argument vs Parameter

- The terms parameter and argument are often used interchangeably in Python, but there is a subtle difference between the two.
- Parameter is a variable defined in the function definition.
- Argument is the value that is passed to the function when it is called.


## Positional and Keyword Arguments

- ***Positional arguments*** are arguments that are passed to a function in the order that they are defined in the function definition. The order of the arguments is important.
- The number of positional arguments must match the number of parameters defined in the function definition.

- ***Keyword arguments*** are passed to a function using the parameter names as keys and the corresponding values.
- This allows you to provide arguments out of order

```python
def greet(name, age):
    print("Hello, " + name + "! You are " + str(age) + " years old.")

greet("Alice", 25)
```

- In this example, "Alice" and 25 are positional arguments that are assigned to the name and age parameters respectively.

```python
greet(age=25, name="Alice")
```

- In this example, name and age are keyword arguments. The values are assigned based on the parameter names, not their position.

- You can ***mix positional and keyword arguments*** in a function call, but positional arguments must come before keyword arguments.
- Once you start using keyword arguments, you ***can't*** switch back to positional arguments.

```python
greet("Alice", age=25)
```

- Here, "Alice" is a positional argument, and age=25 is a keyword argument.
- The position of the positional argument matters, but the keyword argument can be placed after it.


## Default Parameter Values

- You can assign default values to function parameters when you define the function.
- This is done by using the assignment operator = after the parameter name in the function's parameter list.

```python
def greet(name, age=30):
    print("Hello, " + name + "! You are " + str(age) + " years old.")
```

- In this example, age is a parameter with a default value of 30.
- When you call a function with default parameters, you have the option to omit the argument associated with the default value.

```python
greet("Alice")  # Uses default age value (30)
```

- You can still provide an argument to a parameter with a default value to override the default.

```python
greet("Bob", 28)  # Overrides the default age value
```
- When mixing default and non-default parameters, the non-default parameters must come before the default parameters in the function's parameter list.

```python
def greet(name, greeting="Hello"):
    print(greeting + ", " + name + "!")
```

## Quick into into tuples

- Tuples are ordered, immutable sequences, similar to lists, but they are defined using parentheses ().
- Tuples can contain elements of different types, and they are commonly used to group related pieces of data.  
- To define a tuple, you use parentheses () and separate the elements with commas:
```python
# A tuple with three elements
my_tuple = (1, 2, 3)
```
- If you want to define a tuple with a single element, you need to include a comma after the element. This is because parentheses alone would be interpreted as an expression, not a tuple.
```python
# Tuple with a single element
single_element_tuple = (42,)
```
- An empty tuple is defined by using just an empty set of parentheses:
```python
# Empty tuple
empty_tuple = ()
```

## Iterable and Iterator

- An iterable is any Python object capable of returning its elements one at a time, allowing them to be iterated (looped) over using a for loop, while loop, or other iteration mechanisms.
- Common examples of iterables include lists, tuples, strings, dictionaries, and sets.

- An iterator in Python is an object that can be used to iterate over a sequence of elements.
- Iterators are created using the iter() function, and they can be iterated over using a for loop.

```python
list1 = ["apple", "banana", "cherry"]

# Create an iterator for the list
iterator = iter(list1)

# Print the first element in the iterator
print(next(iterator))
print(next(iterator))
print(next(iterator))
```
- This code will print the first element in the list, which is "apple", then the second, then the third.

- Iterators can also be used to iterate over strings, files, and other iterable objects.


## Unpacking Iterables

- Unpacking iterables is the process of assigning the values of an iterable to multiple variables in a single assignment statement.
- This can be done with any iterable, such as lists, tuples, strings, and iterators.

```python
list1 = ["apple", "banana", "cherry"]

# Unpack the list into three variables
a, b, c = list1

# Print the values of the variables
print(a)
print(b)
print(c)
```

## Extended Unpacking

- Extended unpacking is a feature of Python that allows you to unpack an iterable into multiple variables, even if the iterable contains more elements than there are variables.
- This can be done using the * operator and the ** operator.

- The * operator can be used to unpack an iterable into a tuple of variables.
- The number of variables does not have to match the number of elements in the iterable. The excess elements are simply ignored.

```python
list1 = ["apple", "banana", "cherry", "grape"]

# Unpack the list into three variables
a, b, *rest = list1

# Print the values of the variables
print(a)
print(b)
print(rest)
```
- This code will print the following output:
```
apple
banana
['cherry', 'grape']
```

- The ** operator can be used to unpack an iterable into a dictionary of variables.
- The keys of the dictionary do not have to match the names of the variables.
```python
dict1 = {"name": "John Doe", "age": 30, "city": "New York"}

# Unpack the dictionary into two variables
name, **other_details = dict1

# Print the values of the variables
print(name)
print(other_details)
```
- This code will print the following output:
```
John Doe
{'age': 30, 'city': 'New York'}
```

## json.load() vs json.loads() vs json.dump() vs json.dumps()

In Python's `json` module, you have four main functions for working with JSON data:

1. `json.load()`: This function is used to load JSON data from a file-like object (e.g., a file object) into a Python object.

   Example:
   ```python
   import json

   with open('data.json', 'r') as json_file:
       data = json.load(json_file)

   # 'data' now contains a Python object representing the JSON data from 'data.json'
   ```

2. `json.loads()`: This function is used to parse a JSON string and convert it into a Python object.

   Example:
   ```python
   import json

   json_string = '{"name": "John", "age": 30}'
   data = json.loads(json_string)

   # 'data' now contains a Python object representing the JSON data
   ```

3. `json.dump()`: This function is used to write a Python object to a file-like object (e.g., a file) in JSON format.

   Example:
   ```python
   import json

   data = {"name": "John", "age": 30}
   with open('output.json', 'w') as json_file:
       json.dump(data, json_file)

   # This writes the Python 'data' object as a JSON string to 'output.json'
   ```

4. `json.dumps()`: This function is used to convert a Python object into a JSON-formatted string.

   Example:
   ```python
   import json

   data = {"name": "John", "age": 30}
   json_string = json.dumps(data)

   # 'json_string' now contains a JSON-formatted string representation of the Python 'data' object
   ```

In summary:
- Use `load()` and `loads()` when you want to read and parse JSON data into a Python object.
- Use `dump()` and `dumps()` when you want to serialize a Python object into JSON format for writing to a file or sending over a network, or when you need to create a JSON string representation of a Python object.

NOTE: Python object => Python dictionary (dict)

## json.loads() vs dict()

`json.loads()` and `dict()` are indeed similar in that they both can convert a JSON-formatted string into a Python dictionary (`dict`). However, there are some important differences between the two:

1. JSON Validity: `json.loads()` is specifically designed for parsing JSON data, and it enforces strict JSON syntax rules. It will raise an error if the input string is not valid JSON. On the other hand, using `dict()` to convert a JSON string to a dictionary does not perform JSON validation. It assumes that the input is a valid dictionary literal in Python, which can lead to unexpected behavior if the input string is not properly formatted as JSON.

2. Safety: `json.loads()` is safer to use when dealing with untrusted or potentially malicious data. Since it performs JSON validation, it helps protect against common security vulnerabilities like JSON injection attacks. Using `dict()` to parse untrusted JSON strings can potentially execute arbitrary code if the JSON string contains malicious code.

Here's an example illustrating the difference:

```python
import json

json_string = '{"name": "John", "age": 30}'

# Using json.loads() - safe and enforces JSON validity
data_from_json = json.loads(json_string)

# Using dict() - no JSON validation
data_from_dict = dict(eval(json_string))

print(data_from_json)  # Output: {'name': 'John', 'age': 30}
print(data_from_dict)  # Output: {'name': 'John', 'age': 30}

# Now let's try with an invalid JSON string

invalid_json_string = '{"name": "John", "age": 30,}'  # Note the trailing comma

# Using json.loads() - raises a JSONDecodeError
# json.loads(invalid_json_string)

# Using dict() - no error, but may not behave as expected due to the trailing comma
data_from_dict_invalid = dict(eval(invalid_json_string))
print(data_from_dict_invalid)  # Output: {'name': 'John', 'age': 30}
```

In the commented out line, if you uncomment `json.loads(invalid_json_string)`, it will raise a `json.decoder.JSONDecodeError` because of the invalid JSON syntax. However, `dict(eval(invalid_json_string))` does not raise an error, but it may not behave as expected due to the trailing comma in the input string. This demonstrates the importance of using `json.loads()` for safe and reliable JSON parsing.

## how not to mix up load() with loads(), dump() with dumps()

To avoid mixing up `load` with `loads` and `dump` with `dumps`, you can rely on the following logic and mnemonic devices to help remember the differences:

1. **Naming Convention Logic**:

   - **`load`** reads data from a file-like object and **loads** it into a Python object. Think of "load" as in loading data from a file.

   - **`loads`** is similar to `load`, but it operates on a **string** and **loads** the JSON data from the string into a Python object. Think of "loads" as in loading from a string.

   - **`dump`** writes data from a Python object and **dumps** it into a file-like object (e.g., a file). Think of "dump" as in dumping data into a file.

   - **`dumps`** is similar to `dump`, but it operates on a Python object and **dumps** the Python data as a JSON-formatted **string**. Think of "dumps" as in dumping to a string.

2. **Mnemonic Devices**:

   - **Load vs. Loads**:
     - Think of "s" in "loads" as standing for "string." `loads` works with JSON data in string form.

   - **Dump vs. Dumps**:
     - Think of "s" in "dumps" as standing for "string." `dumps` generates a JSON string from Python data.

Here's a mnemonic device to remember the entire set:

- "Load" and "loads" both deal with loading data into Python. One reads from a file-like object, and the other reads from a string.

- "Dump" and "dumps" both deal with dumping data out of Python. One writes to a file-like object, and the other writes to a string.

By using these naming conventions and mnemonics, you can better remember which function to use in different situations. Practice and familiarity will also reinforce your understanding over time.

## how import works

In Python, the `import` statement is used to include external modules or packages in your code, allowing you to use the functions, classes, and variables defined within those modules. Here's how the `import` statement works:

1. **Importing a Module**:

   You can import an entire module by specifying its name after the `import` keyword. For example, to import the `math` module, you can do:

   ```python
   import math
   ```

   After this import statement, you can access functions and variables defined in the `math` module using dot notation, like `math.sqrt(25)`.

2. **Importing Specific Items from a Module**:

   You can also import specific functions, classes, or variables from a module using the `from` keyword. For example, to import only the `sqrt` function from the `math` module:

   ```python
   from math import sqrt
   ```

   Now, you can use `sqrt(25)` directly without referencing `math`.

3. **Renaming Imported Modules or Items**:

   You can rename a module or item during import using the `as` keyword. This is useful when you want to avoid naming conflicts or create shorter aliases for module names. For example:

   ```python
   import math as m  # Renaming 'math' module to 'm'
   ```

   You can then use `m.sqrt(25)` instead of `math.sqrt(25)`.

4. **Importing Everything from a Module (Not Recommended)**:

   You can use the `*` wildcard to import all items from a module into the current namespace. However, this is generally discouraged because it can lead to naming conflicts and make your code less readable. For example:

   ```python
   from math import *
   ```

   Avoid using `import *` in production code, especially when working on large projects.

5. **Importing from Packages**:

   Python allows you to organize modules into packages, which are directories containing a special `__init__.py` file. You can import modules and submodules from packages using dot notation. For example:

   ```python
   from mypackage import module1
   from mypackage.subpackage import module2
   ```

   In this example, `module1` and `module2` are modules within the `mypackage` package and its `subpackage`.


The `import` statement is a fundamental part of Python's modular approach, allowing you to break your code into reusable and organized components. Properly structuring and managing imports is important for code clarity, maintainability, and avoiding naming conflicts.

## any() and all()

In Python, `any()` and `all()` are built-in functions that are used to evaluate sequences (like lists, tuples, or other iterable objects) in a logical context. They return `True` or `False` based on the elements in the sequence. Here's how `any()` and `all()` work:

1. **`any(iterable)`**:

   - The `any()` function returns `True` if at least one element in the iterable is `True` (or evaluates to `True` in a boolean context).
   - If all elements in the iterable are `False` (or evaluate to `False`), it returns `False`.
   - If the iterable is empty, it also returns `False`.

   Example:

   ```python
   # Check if any element in the list is even
   numbers = [1, 3, 5, 8, 9]
   result = any(x % 2 == 0 for x in numbers)
   print(result)  # Output: True
   ```

2. **`all(iterable)`**:

   - The `all()` function returns `True` if all elements in the iterable are `True` (or evaluate to `True` in a boolean context).
   - If any element in the iterable is `False` (or evaluates to `False`), it returns `False`.
   - If the iterable is empty, it returns `True` (because there are no `False` elements to contradict it).

   Example:

   ```python
   # Check if all elements in the list are even
   numbers = [2, 4, 6, 8, 10]
   result = all(x % 2 == 0 for x in numbers)
   print(result)  # Output: True
   ```

Both `any()` and `all()` are often used in conditional statements and loops to evaluate the truthiness or falsiness of elements in a sequence. They can simplify code by providing concise ways to check conditions across multiple elements.


## list comprehension

List comprehensions provide a concise way to create lists in Python by applying an expression to each item in an iterable (e.g., a list, tuple, or range) and optionally filtering the items based on a condition. The basic structure of a list comprehension is:

```
[expression for item in iterable if condition]
```

Let's break down how a list comprehension works and understand its workflow:

1. **Iterating Over the Iterable**:

   The list comprehension starts by iterating over each item in the specified iterable (e.g., a list or range). For each item in the iterable, it evaluates the expression and, if a condition is provided, checks if the condition is `True` for that item.

2. **Applying the Expression**:

   For each item in the iterable, the expression specified in the comprehension is applied. This expression defines what will be included in the new list. The result of the expression for each item is added to the new list.

3. **Conditionally Filtering Items** (Optional):

   If a condition is specified in the list comprehension (after the `if` keyword), it is evaluated for each item in the iterable. Only items for which the condition is `True` are included in the new list. If no condition is provided, all items from the iterable are included by default.

4. **Creating the New List**:

   The list comprehension collects the results of applying the expression to the items that meet the condition (if a condition is provided) and creates a new list with those results.

Here's a step-by-step example to illustrate the workflow of a list comprehension:

```python
# Example: Create a list of squares for even numbers in the range 1 to 10
numbers = range(1, 11)
squares_of_evens = [x**2 for x in numbers if x % 2 == 0]

# Workflow:
# 1. Iterate over the numbers 1 to 10.
# 2. For each number, apply the expression x**2.
# 3. Check if the condition x % 2 == 0 is met.
# 4. If the condition is met, add the result of x**2 to the new list.
# 5. Continue this process for all numbers in the range.
# 6. The result is a new list containing the squares of even numbers.

# Result: squares_of_evens is [4, 16, 36, 64, 100]
```

Here are some examples of list comprehensions:

**Example 1: Creating a list of squares**

Using a list comprehension to create a list of squares of numbers from 0 to 9:

```python
squares = [x**2 for x in range(10)]
# Result: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

**Example 2: Filtering even numbers**

Using a list comprehension to create a list of even numbers from a given list:

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = [x for x in numbers if x % 2 == 0]
# Result: [2, 4, 6, 8, 10]
```

**Example 3: Creating a list of tuples**

Using a list comprehension to create a list of tuples containing the square and cube of each number from 1 to 5:

```python
pairs = [(x, x**2, x**3) for x in range(1, 6)]
# Result: [(1, 1, 1), (2, 4, 8), (3, 9, 27), (4, 16, 64), (5, 25, 125)]
```

**Example 4: Flattening a 2D list**

Using a list comprehension to flatten a 2D list into a single list:

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat_matrix = [element for row in matrix for element in row]
# Result: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

**Example 5: Converting strings to uppercase**

Using a list comprehension to convert a list of strings to uppercase:

```python
words = ['apple', 'banana', 'cherry']
uppercase_words = [word.upper() for word in words]
# Result: ['APPLE', 'BANANA', 'CHERRY']
```

**Example 6: Filtering and modifying a list**

Using a list comprehension to filter and modify elements in a list:

```python
numbers = [1, 2, 3, 4, 5]
modified_numbers = [x * 2 if x % 2 == 0 else x for x in numbers]
# Result: [1, 4, 3, 8, 5]
```

List comprehensions offer a concise way to create lists, and they can often replace complex `for` loops with a more readable and Pythonic syntax. They are widely used in Python for data manipulation and transformation.

## reversing list elements

You can reverse the elements of a list in Python using multiple methods. Here are three common approaches:

1. Using the `reverse()` method:
   You can use the `reverse()` method to reverse the elements of a list in-place. This means that the original list is modified, and the order of its elements is reversed.

   ```python
   my_list = [1, 2, 3, 4, 5]
   my_list.reverse()

   # 'my_list' is now [5, 4, 3, 2, 1]
   ```

2. Using slicing:
   You can use slicing to create a new list with the elements in reverse order. This approach does not modify the original list.

   ```python
   my_list = [1, 2, 3, 4, 5]
   reversed_list = my_list[::-1]

   # 'my_list' is still [1, 2, 3, 4, 5], while 'reversed_list' is [5, 4, 3, 2, 1]
   ```

3. Using the `reversed()` function:
   The `reversed()` function returns a reverse iterator, which can be converted into a list using `list()`.

   ```python
   my_list = [1, 2, 3, 4, 5]
   reversed_list = list(reversed(my_list))

   # 'my_list' is still [1, 2, 3, 4, 5], while 'reversed_list' is [5, 4, 3, 2, 1]
   ```

Choose the method that best suits your needs. If you want to reverse the original list in-place, use the `reverse()` method. If you want to keep the original list unchanged and create a new reversed list, use slicing or the `reversed()` function.
