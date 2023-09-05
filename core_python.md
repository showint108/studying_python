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
