# Python - Exceptions

## What’s the difference between errors and exceptions

In Python, errors and exceptions are both types of issues that can occur during the execution of a program, but they are distinct in nature.

1. Errors: Errors are typically caused by flaws in the code or its structure, preventing the program from executing properly. They are divided into three main types:

   a. Syntax Errors: Syntax errors occur when the code violates the rules of the Python language grammar. These errors are usually detected by the Python interpreter during the parsing phase, before the code is executed. Common examples include missing colons, mismatched parentheses, or using invalid keywords.

   b. Logical Errors: Logical errors, also known as bugs, occur when the code does not produce the expected or correct output due to flawed logic or algorithmic mistakes. These errors are not detected by the interpreter and may require debugging and careful analysis to identify and fix.

   c. Runtime Errors: Runtime errors, also called exceptions, occur during the execution of a program when an unexpected condition or situation arises. They are caused by factors such as invalid user input, division by zero, or accessing a non-existent variable or object.

2. Exceptions: Exceptions are a specific type of runtime error in Python. When an exception occurs, it disrupts the normal flow of the program and can be caught and handled using exception handling mechanisms. Exceptions are typically caused by external factors or runtime conditions that the programmer may not have anticipated or controlled.

   Python provides a range of built-in exceptions that cover various error scenarios. Examples include `ZeroDivisionError` (division by zero), `TypeError` (mismatched types), `ValueError` (invalid argument value), and `FileNotFoundError` (file not found), among others. Additionally, you can create custom exceptions by deriving them from the base `Exception` class.

To handle exceptions, you can use try-except blocks to catch and handle specific exceptions gracefully. By using exception handling, you can provide alternative actions or error messages, gracefully exit the program, or perform any necessary cleanup operations.

Here's an example of how exception handling can be used in Python:

```python
try:
    # Code that may raise an exception
    result = 10 / 0  # Raises ZeroDivisionError
except ZeroDivisionError:
    # Exception handling code
    print("Error: Division by zero occurred.")
```

In the example above, the `try` block attempts to divide 10 by 0, which raises a `ZeroDivisionError`. The `except` block catches the specific exception, allowing you to handle it appropriately.

## What are exceptions and how to use them

In Python, exceptions are a way to handle and manage errors or exceptional conditions that occur during the execution of a program. When an exceptional situation arises, such as division by zero or accessing a non-existent file, an exception is raised, which interrupts the normal flow of the program. By using exception handling, you can catch and handle these exceptions gracefully, allowing your program to continue running or perform alternative actions.

Here's an overview of how to use exceptions in Python:

1. Raising Exceptions:
   You can raise an exception explicitly using the `raise` statement. This is useful when you want to indicate that a certain condition has occurred that warrants an exceptional behavior. You can raise built-in exceptions or create custom exceptions by deriving from the base `Exception` class.

   Example:
   ```python
   raise ValueError("Invalid input provided.")
   ```

2. Handling Exceptions:
   You can handle exceptions using `try-except` blocks. The `try` block contains the code that may raise an exception. If an exception is raised, it is caught by the corresponding `except` block. You can have multiple `except` blocks to handle different types of exceptions.

   Example:
   ```python
   try:
       # Code that may raise an exception
       result = 10 / 0  # Raises ZeroDivisionError
   except ZeroDivisionError:
       # Exception handling code
       print("Error: Division by zero occurred.")
   ```

3. Handling Multiple Exceptions:
   You can handle multiple exceptions by including multiple `except` blocks. Each `except` block specifies the type of exception it can handle. If an exception matches any of the specified types, the corresponding block is executed.

   Example:
   ```python
   try:
       # Code that may raise an exception
       file = open("nonexistent_file.txt")
   except FileNotFoundError:
       # Exception handling for file not found
       print("Error: File not found.")
   except PermissionError:
       # Exception handling for permission denied
       print("Error: Permission denied.")
   ```

4. Exception Hierarchy:
   In Python, exceptions are organized in a hierarchy. The base class for all exceptions is `BaseException`, which is further subclassed into various specific exception classes. You can catch multiple exceptions using a single `except` block by specifying the common base class.

   Example:
   ```python
   try:
       # Code that may raise an exception
       result = some_function()
   except Exception as e:
       # Exception handling for any exception
       print("An exception occurred:", str(e))
   ```

5. The `finally` Block:
   You can optionally include a `finally` block after the `try-except` blocks. The code inside the `finally` block is executed regardless of whether an exception occurred or not. It is typically used to perform cleanup operations, such as closing files or releasing resources.

   Example:
   ```python
   try:
       # Code that may raise an exception
       file = open("data.txt")
       # Process the file
   except FileNotFoundError:
       print("Error: File not found.")
   finally:
       # Cleanup code
       if file:
           file.close()
   ```

By using exceptions and exception handling in your Python code, you can effectively deal with errors and exceptional situations, making your programs more robust and reliable.

## When do we need to use exceptions

Exceptions in Python are used to handle and manage errors or exceptional situations that may occur during the execution of a program. Here are some common scenarios where you would need to use exceptions:

1. Error Handling:
   Exceptions are primarily used for error handling. When you anticipate that certain operations in your code may encounter errors or exceptional conditions, you can use exception handling to gracefully handle those situations. This allows you to prevent your program from crashing and provides the opportunity to handle errors in a controlled manner.

2. Input Validation:
   Exceptions can be used to validate user input. When you expect a specific type of input or a particular format, you can check the input and raise an exception if it doesn't meet the expected criteria. This allows you to handle invalid or unexpected input and provide appropriate feedback to the user.

3. File Operations:
   When working with files, exceptions can be used to handle various file-related errors. For example, when opening a file, exceptions like `FileNotFoundError` or `PermissionError` may occur if the file doesn't exist or if the user doesn't have the necessary permissions. By catching these exceptions, you can handle the errors gracefully, display appropriate error messages, or take alternative actions.

4. Networking and I/O Operations:
   Exceptions are commonly used when performing networking operations or input/output (I/O) operations, such as reading from or writing to files or interacting with databases. These operations can encounter errors like connection failures, timeouts, or invalid data. By handling the corresponding exceptions, you can manage these errors and ensure that your program handles such situations gracefully.

5. Resource Cleanup:
   Exceptions, along with the `finally` block, are useful for resource cleanup. If your code acquires resources like file handles, database connections, or network sockets, it's important to release those resources properly, even in the presence of exceptions. The `finally` block allows you to write cleanup code that is executed regardless of whether an exception occurred or not, ensuring proper resource management.

6. Custom Error Conditions:
   In addition to built-in exceptions, you can define custom exceptions specific to your program's requirements. This is useful when you want to communicate application-specific error conditions to the calling code or provide a more descriptive context for the encountered exception.

By using exceptions in these scenarios, you can enhance the robustness and reliability of your Python programs. They enable you to handle errors gracefully, provide meaningful feedback to users, ensure proper resource management, and control the flow of your program in exceptional situations.

## How to correctly handle an exception

To correctly handle an exception in Python, you can use a combination of the `try`, `except`, and `finally` blocks. Here's a step-by-step guide on how to handle exceptions effectively:

1. Identify the Code that May Raise an Exception:
   Review your code and identify the specific section where an exception may occur. This could be a block of code that performs operations that are prone to errors, such as input validation, file operations, or network communication.

2. Wrap the Risky Code in a Try Block:
   Place the risky code inside a `try` block. The `try` block allows you to define the section of code that needs exception handling. If an exception occurs within this block, it will be caught by the corresponding `except` block.

   Example:
   ```python
   try:
       # Risky code that may raise an exception
       result = 10 / 0  # Raises ZeroDivisionError
   ```

3. Define the Appropriate Exception Handlers:
   Immediately after the `try` block, include one or more `except` blocks to handle specific types of exceptions that might occur. Each `except` block specifies the type of exception it can handle.

   Example:
   ```python
   except ZeroDivisionError:
       # Exception handling for ZeroDivisionError
       print("Error: Division by zero occurred.")
   ```

   You can have multiple `except` blocks to handle different types of exceptions. If an exception occurs that matches any of the specified types, the corresponding `except` block is executed.

4. Handle or Process the Exception:
   Inside the `except` block, you can handle the exception by providing appropriate error messages, performing alternative actions, or taking corrective measures. This could involve logging the error, displaying user-friendly messages, or attempting to recover from the error.

   Example:
   ```python
   except ZeroDivisionError:
       # Exception handling for ZeroDivisionError
       print("Error: Division by zero occurred.")
       # Perform alternative actions or error recovery
   ```

5. Include a Finally Block (Optional):
   Optionally, you can include a `finally` block after the `try-except` blocks. The code inside the `finally` block is executed regardless of whether an exception occurred or not. It is typically used to perform cleanup operations, such as closing files or releasing resources.

   Example:
   ```python
   finally:
       # Cleanup code
       # This block is executed whether an exception occurred or not
   ```

   The `finally` block is useful for ensuring that certain actions are always performed, regardless of whether an exception is raised or not.

By following these steps, you can handle exceptions effectively and ensure that your program continues to run smoothly even in the presence of errors. Exception handling allows you to control the flow of your program, provide appropriate error feedback, and handle exceptional situations gracefully.

## What’s the purpose of catching exceptions

The purpose of catching exceptions in Python is to handle errors or exceptional situations that may occur during the execution of a program. By catching exceptions, you can:

1. Prevent Program Crashes: Exceptions, if left unhandled, can cause your program to terminate abruptly. By catching exceptions, you can prevent your program from crashing and provide a controlled way to handle the error.

2. Graceful Error Handling: When an exception is raised, you have the opportunity to handle it gracefully. You can provide meaningful error messages, log the error for later analysis, or take alternative actions to recover from the error.

3. Provide User-Friendly Feedback: When your program encounters an error, catching the exception allows you to display user-friendly error messages instead of exposing technical details. This improves the user experience by providing clearer instructions or suggestions on how to resolve the issue.

4. Control Program Flow: Exception handling allows you to control the flow of your program in exceptional situations. You can define specific actions to be taken when certain exceptions occur, enabling you to handle different scenarios appropriately.

5. Resource Cleanup: Exception handling, along with the `finally` block, enables you to ensure proper cleanup and release of resources, such as closing files, releasing database connections, or cleaning up allocated memory. The `finally` block is executed whether an exception occurred or not, providing a reliable mechanism for performing necessary cleanup operations.

6. Handle Specific Exception Types: By catching specific types of exceptions, you can handle different error scenarios differently. This allows you to provide tailored error handling for each type of exception, addressing the specific needs of different error conditions.

7. Recovery and Error Correction: In some cases, you may be able to recover from an exception or correct the error condition. By catching the exception, you can attempt error recovery, retry failed operations, or provide an alternative approach to achieve the desired outcome.

Overall, catching exceptions allows you to respond to errors in a controlled manner, improve the user experience, ensure proper resource management, and maintain the stability and reliability of your program. It provides a mechanism to handle exceptional situations, enabling your program to gracefully recover or exit if necessary.

## How to raise a builtin exception

To raise a built-in exception in Python, you can use the `raise` statement followed by the specific exception class or type. Here's the general syntax:

```python
raise ExceptionClassName("Error message")
```

You replace `ExceptionClassName` with the name of the built-in exception class you want to raise, and `"Error message"` with a descriptive error message explaining the reason for the exception.

Here are a few examples of raising common built-in exceptions:

1. Raising a `ValueError`:
   ```python
   raise ValueError("Invalid value provided.")
   ```

2. Raising a `TypeError`:
   ```python
   raise TypeError("Invalid type.")
   ```

3. Raising a `FileNotFoundError`:
   ```python
   raise FileNotFoundError("File not found.")
   ```

4. Raising an `IndexError`:
   ```python
   raise IndexError("List index out of range.")
   ```

5. Raising a `KeyError`:
   ```python
   raise KeyError("Key not found in dictionary.")
   ```

You can also raise custom exceptions by creating a new exception class that inherits from the base `Exception` class. Here's an example:

```python
class CustomException(Exception):
    pass

raise CustomException("Custom exception raised.")
```

In this example, a custom exception class named `CustomException` is defined by inheriting from `Exception`. Then, an instance of `CustomException` is raised with a custom error message.

By raising built-in exceptions, you can communicate specific error conditions to the calling code or handle exceptional situations in a consistent and recognizable manner.

## When do we need to implement a clean-up action after an exception

Implementing a clean-up action after an exception is necessary when your code acquires resources, such as opening files, establishing database connections, or allocating memory, that need to be properly released or cleaned up, even in the presence of an exception. The clean-up action ensures that resources are properly managed and avoids potential issues like resource leaks or inconsistent program states.

Here are a few scenarios where implementing a clean-up action after an exception is important:

1. File Operations:
   When your code opens files for reading or writing, it's crucial to close the files properly, regardless of whether an exception occurs or not. Failing to close files can result in resource leaks and may prevent other processes from accessing those files.

   Example:
   ```python
   try:
       file = open("data.txt")
       # Perform file operations
   except FileNotFoundError:
       print("Error: File not found.")
   finally:
       if file:
           file.close()  # Clean-up: Close the file
   ```

2. Database Connections:
   When working with databases, it's important to release database connections properly, even if exceptions occur. Leaving connections open can exhaust available connections or cause other issues in the database server.

   Example:
   ```python
   try:
       conn = establish_database_connection()
       # Perform database operations
   except ConnectionError:
       print("Error: Connection failed.")
   finally:
       if conn:
           conn.close()  # Clean-up: Close the connection
   ```

3. Memory Allocation:
   If your code dynamically allocates memory using techniques like `malloc` or `new`, it's crucial to deallocate the memory properly, even in the presence of exceptions. Failing to release memory can result in memory leaks and adversely impact the performance of your program.

   Example:
   ```python
   try:
       buffer = allocate_memory()
       # Perform operations with allocated memory
   except MemoryError:
       print("Error: Memory allocation failed.")
   finally:
       if buffer:
           deallocate_memory(buffer)  # Clean-up: Deallocate memory
   ```

4. Resource Locks:
   In scenarios where your code acquires locks or synchronization primitives, such as mutexes or semaphores, it's important to release those locks properly to prevent deadlocks or resource contention issues.

   Example:
   ```python
   lock = acquire_lock()
   try:
       # Perform operations protected by the lock
   finally:
       release_lock(lock)  # Clean-up: Release the lock
   ```

By implementing clean-up actions after an exception, you ensure proper resource management, prevent resource leaks, and maintain the stability and reliability of your program. The `finally` block is particularly useful for including clean-up code that is always executed, regardless of whether an exception occurred or not.
