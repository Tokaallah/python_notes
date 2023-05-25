# Python - import & modules

In Python, modules are files containing Python definitions and statements that can be used in other Python programs. They allow you to organize your code into reusable and manageable units. You can import modules into your Python scripts using the `import` statement.

There are different ways to import modules in Python:

1. Importing the entire module:
   ```python
   import module_name
   ```
   This allows you to access functions, classes, and variables defined in the module using the `module_name` prefix.

2. Importing specific items from a module:
   ```python
   from module_name import item_name
   ```
   This imports a specific function, class, or variable from the module, allowing you to use it directly without the need for the `module_name` prefix.

3. Importing all items from a module:
   ```python
   from module_name import *
   ```
   This imports all functions, classes, and variables from the module, allowing you to use them directly without the need for the `module_name` prefix. However, it's generally recommended to avoid this approach to prevent name clashes and improve code readability.

Once you have imported a module, you can use its functions, classes, and variables in your code. Here's an example:

```python
# Importing the entire module
import math

# Using a function from the math module
print(math.sqrt(16))

# Importing a specific function from the math module
from math import factorial

# Using the factorial function directly
print(factorial(5))
```

It's also worth mentioning that you can create your own modules by defining functions, classes, and variables in a Python file and then importing them in other scripts.

I hope this helps! Let me know if you have any further questions.

## How to import functions from another file

To import functions from another file in Python, you can use the `import` statement. Here's a step-by-step guide on how to do it:

1. Create a Python file (let's call it `my_functions.py`) that contains the functions you want to import. For example:

   ```python
   # my_functions.py

   def greet(name):
       print(f"Hello, {name}!")

   def add_numbers(a, b):
       return a + b
   ```

2. In your main Python script, use the `import` statement to import the functions from `my_functions.py`. For example:

   ```python
   # main_script.py

   from my_functions import greet, add_numbers

   greet("John")  # Call the greet function from my_functions.py
   result = add_numbers(5, 7)  # Call the add_numbers function from my_functions.py
   print(result)
   ```

   In this example, we import the `greet` and `add_numbers` functions from the `my_functions` module. Now you can use these functions directly in your `main_script.py`.

3. Run your main script (`main_script.py`), and it will call the imported functions as expected.

Note that when importing functions from another file, make sure that the file (`my_functions.py` in this example) is in the same directory as your main script or accessible through the Python module search path.

Additionally, you can import all the functions from the file by using `from my_functions import *`. However, it is generally considered better practice to import specific functions to avoid potential naming conflicts and improve code readability.

I hope this clarifies how to import functions from another file in Python. Let me know if you have any further questions!

## How to create a module

Creating a module in Python is quite simple. Here's a step-by-step guide on how to create your own module:

1. Create a new Python file in your desired location. Let's name it `my_module.py`.

2. Define functions, classes, and/or variables in the `my_module.py` file. For example:

   ```python
   # my_module.py

   def greet(name):
       print(f"Hello, {name}!")

   def add_numbers(a, b):
       return a + b

   my_variable = 42
   ```

   In this example, we have defined two functions (`greet` and `add_numbers`) and a variable (`my_variable`) within the `my_module.py` file.

3. Save the `my_module.py` file.

That's it! You have created your own module. You can now import and use the functions and variables defined in `my_module.py` in other Python scripts.

To use the module in another script, follow these steps:

1. Create a new Python script in the same directory (or in a directory accessible through the Python module search path). Let's name it `main_script.py`.

2. Import the module using the `import` statement:

   ```python
   # main_script.py

   import my_module
   ```

   This imports the `my_module` module, making its functions and variables accessible using the `my_module` prefix.

3. Use the functions and variables defined in `my_module` as needed:

   ```python
   # main_script.py

   my_module.greet("John")  # Call the greet function from my_module
   result = my_module.add_numbers(5, 7)  # Call the add_numbers function from my_module
   print(result)

   print(my_module.my_variable)  # Access the my_variable defined in my_module
   ```

   In this example, we call the `greet` and `add_numbers` functions from `my_module`, as well as access the `my_variable` defined within the module.

4. Run the `main_script.py` script, and it will utilize the functions and variables from the `my_module` module.

That's how you can create a module in Python and use it in your code. Modules are a great way to organize and reuse your code across multiple scripts.

I hope this explanation helps you! Let me know if you have any further questions.

## How to use the built-in function dir()

The built-in function `dir()` in Python is used to list the names in the current scope or to retrieve the attributes of an object. It can be helpful for exploring the contents of a module, class, or any other Python object. Here's how you can use the `dir()` function:

1. To list the names in the current scope:
   When called without any arguments, `dir()` returns a sorted list of names in the current module or the current scope. For example:

   ```python
   # main_script.py

   import math

   names = dir()
   print(names)
   ```

   In this example, `dir()` is called without any arguments in the `main_script.py` file. It will return a sorted list of names in the current scope, which includes the names of built-in functions, variables, imported modules (like `math`), and any other names defined in the script.

2. To retrieve the attributes of an object:
   When called with an object as an argument, `dir(object)` returns a sorted list of valid attributes and methods of that object. For example:

   ```python
   # main_script.py

   import math

   attributes = dir(math)
   print(attributes)
   ```

   In this example, `dir(math)` is used to retrieve the attributes of the `math` module. It will return a sorted list of the valid attributes and functions available in the `math` module.

The `dir()` function can be handy when you want to explore the available names in a module or the attributes of an object dynamically. It's particularly useful during development and debugging stages.

Keep in mind that some objects may not provide a complete list of their attributes. Certain objects may implement the `__dir__()` method to customize the behavior of `dir()`.

I hope this clarifies how to use the `dir()` function in Python. Let me know if you have any further questions!

## How to prevent code in your script from being executed when imported

In Python, you can prevent certain code in a script from being executed when it is imported by using the `__name__` variable. The `__name__` variable holds the name of the current module.

When a script is run directly as the main module, `__name__` is set to `'__main__'`. However, when a script is imported as a module in another script, `__name__` is set to the actual name of the module. By leveraging this behavior, you can conditionally execute code only when the script is run directly.

Here's an example of how to prevent code from being executed when imported:

```python
# my_script.py

def some_function():
    # Code to be executed when the script is imported or run directly
    pass

def main():
    # Code to be executed when the script is run directly
    pass

if __name__ == "__main__":
    main()
```

In this example, the code inside the `if __name__ == "__main__":` block will only be executed when the script is run directly. If the script is imported as a module in another script, that block will be skipped.

By organizing your code in this manner, you can have certain code executed only when the script is intended to be run directly. The other functions and code in the script can still be imported and used by other modules without being executed immediately.

This approach is often used to separate script functionality from reusable module functionality. It allows you to have executable code in the script for testing and development purposes while keeping the reusable parts accessible to other modules.

I hope this answers your question! Let me know if you have any further doubts.

## How to use command line arguments with your Python programs

In Python, you can use the `sys.argv` list to access command line arguments passed to your Python program. The `sys.argv` list contains the command line arguments, with the first element (`sys.argv[0]`) being the name of the Python script itself.

Here's an example of how to use command line arguments in a Python program:

```python
# my_program.py

import sys

# Access command line arguments
arguments = sys.argv

# Check if any arguments were provided
if len(arguments) > 1:
    # Iterate over the command line arguments
    for argument in arguments[1:]:
        print(f"Argument: {argument}")
else:
    print("No arguments provided.")
```

In this example, the program imports the `sys` module to access the `sys.argv` list. It checks if any arguments were provided by checking the length of the list (`len(arguments)`). If there are more than one element in the list, it means arguments were provided. The program then iterates over the arguments starting from index 1 (to skip the script name) and prints each argument. If no arguments were provided, it prints a message stating so.

Now, you can run this Python program with command line arguments like this:

```bash
$ python my_program.py arg1 arg2 arg3
```

The output will be:

```
Argument: arg1
Argument: arg2
Argument: arg3
```

Each argument you provide after the script name will be accessible in the `sys.argv` list.

Note that the command line arguments are always passed as strings. If you need to convert them to other data types, you can use appropriate conversion functions like `int()`, `float()`, etc.

Remember to import the `sys` module at the beginning of your script to use `sys.argv`.

I hope this helps you understand how to use command line arguments with your Python programs. If you have any more questions, feel free to ask!
