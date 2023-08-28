## argparse

- Argparse allows you to define command-line arguments, their types, descriptions, default values, and more.
- It is a Python module in the standard library.

##### Basic Usage:
- Import the Module:

```python
import argparse
```

- Create an ArgumentParser object, which will handle parsing the command-line arguments:

```python
parser = argparse.ArgumentParser(description="Description of your program.")
```
- The description parameter provides a brief overview of your program that will be displayed in the help message.
- Use the .add_argument() method to define the arguments your program accepts. You can specify the argument's name (long or short), its type, help message, default value, and more.

```python
parser.add_argument('--input', type=str, help='Input file path')
parser.add_argument('--output', type=str, help='Output file path')
parser.add_argument('--verbose', action='store_true', help='Enable verbose mode')
```

- In this example, three arguments are defined:

--input: A string-type argument that expects an input file path.  
--output: A string-type argument that expects an output file path.  
--verbose: A boolean-type argument that enables verbose mode.  

- Use the .parse_args() method to parse the command-line arguments provided by the user:

```python
args = parser.parse_args()
```

- The args object holds the parsed argument values.
- You can access the values of the parsed arguments through the args object:

```python
input_file = args.input
output_file = args.output
verbose_mode = args.verbose
```

- Users can provide the defined arguments along with their values when running the program:

```python
python your_program.py --input input.txt --output output.txt --verbose
```

- Users can access a help message by running your program with the --help flag:

```python
python your_program.py --help
```
