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

- The terms parameter and argument are often used interchangeably in Python, but there is a subtle difference between the two.
- Parameter is a variable defined in the function definition.
- Argument is the value that is passed to the function when it is called.


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
