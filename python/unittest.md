# What is a Mock Object in Unit Testing?
A **mock object** is a simulated object that mimics the behavior of a real object in a controlled way. Mock objects are primarily used in unit testing to:
1.	Isolate the code under test from external dependencies.
2.	Verify interactions (e.g., method calls, arguments) with those dependencies.
3.	Simulate specific behaviors or scenarios (e.g., returning predefined values, raising exceptions).

Mock objects allow you to focus on testing your unit of code without relying on the actual implementation or state of the dependencies. This improves test reliability, reduces complexity, and allows for testing edge cases.

# Why it is worth to run pytest with flag -v?
The ```-v``` flag in pytest stands for verbose mode. When you run pytest with the ```-v``` flag, it provides more detailed output about the tests being executed. Here’s what it does:
* Instead of showing only a summary of the test results, ```-v``` displays the names of all the individual test functions as they are executed, along with their status (e.g., passed, failed, or skipped).
  * Example output without ```-v```:

    ```
    ========================== test session starts ==========================
    ========================== 3 passed in 0.02s ============================
    ```
   * Example output with ```-v```:
    ```
    ========================== test session starts ==========================
    test_example.py::test_addition PASSED                             [ 33%]
    test_example.py::test_subtraction PASSED                          [ 66%]
    test_example.py::test_multiplication PASSED                       [100%]
    ========================== 3 passed in 0.02s ============================
    ```
