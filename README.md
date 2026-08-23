# Python Complete Study Notes
### A Standalone Reference — From Basics to OOP

---

## Table of Contents
1. [Introduction to Python](#1-introduction-to-python)
2. [Control Structures](#2-control-structures)
3. [Loops](#3-loops)
4. [Functions](#4-functions)
5. [Strings, Lists, and Tuples](#5-strings-lists-and-tuples)
6. [Sets and Dictionaries](#6-sets-and-dictionaries)
7. [Recursion](#7-recursion)
8. [File Handling and Exception Handling](#8-file-handling-and-exception-handling)
9. [Introduction to OOP](#9-introduction-to-oop)
10. [Inheritance and Polymorphism](#10-inheritance-and-polymorphism)

---

## 1. Introduction to Python

### 1.1 Compiled vs Interpreted Languages
- **Compiler**: Reads the *entire* program at once and takes longer to analyze the source code before producing an output.
- **Interpreter**: Reads and executes code *line by line*, taking very little time to analyze each line.
- **Speed**: Compiled code generally runs faster than interpreted code, because translation to machine code happens once, in advance.
- **Error reporting**: A compiler reports all errors only after full compilation (code won't run if there are mistakes). An interpreter reports errors line by line, stopping as soon as it hits one.
- Python is an **interpreted** language.

> **AI Example/Explanation:** Think of a compiler like a translator who reads an entire book first, translates it completely, and only then hands you the finished translated book — if there's a typo anywhere, you get nothing until it's fixed. An interpreter is more like someone translating a speech live, sentence by sentence, as the speaker talks — you get partial output immediately, but if a sentence has an error, everything stops right there.

### 1.2 Variables
- A **variable** is a name given to a memory location that stores a value.
- Example: in `Monday = 176`, `Monday` is a variable holding the value `176`.

### 1.3 Identifiers
- **Identifiers** (or symbols) are the names you assign to variables, functions, classes, etc.
- Rules for valid identifiers:
  - Cannot start with a digit (e.g., `1var = "Sales"` → `SyntaxError`)
  - Cannot contain a hyphen (e.g., `our-var = "IT"` → `SyntaxError`, since `-` is interpreted as subtraction)
  - Cannot contain a space (e.g., `our var = "Marketing"` → `SyntaxError`)
  - Can contain letters, digits, and underscores, but cannot start with a digit
  - Are **case-sensitive** — `VAR` and `var` are different identifiers

### 1.4 The `print()` Function
- Used to output/display values to the console.
```python
cookies = 10
print(cookies)
```

### 1.5 Comments
Two types:
1. **Single-line comment** — starts with `#`
2. **Multi-line comment** — enclosed within triple quotes `"""..."""`

```python
# This is a single-line comment
Monday = 176    # attendance for monday

"""
This is a multi-line comment
It spans multiple lines
"""
```
- A commented-out variable can no longer be referenced. Trying to use it will raise a `NameError`.

### 1.6 Taking User Input
- `input()` always returns a **string**, even if the user enters a number.
- To take numeric input, wrap `input()` with `int()` or `float()`.

```python
name = input("Enter your name: ")           # basic string input
age = int(input("Enter your age: "))        # numeric input
first_name = input("Enter your first name: ")
last_name = input("Enter your last name: ")
```

> **AI Example/Explanation:** `input()` is like a form field that only accepts plain text — even if someone types "25", Python sees it as the *text* `"25"`, not the *number* `25`. That's why you need `int(input(...))` to convert it: read the text, then convert.

### 1.7 Formatting Output
Two common ways:
1. **f-strings** (formatted string literals) — prefix the string with `f`, and embed variables in `{}`.
2. **`.format()` method** — replaces `{}` placeholders with arguments passed to `.format()`.

```python
name = "Raj"
age = 20
print(f"Name: {name}, Age: {age}")

item = "apple"
price = 0.4534
print("Item: {}, Price: ${:.2f}".format(item, price))
# Output: Item: apple, Price: $0.45
```
- `{:.2f}` formats a float to 2 decimal places.

### 1.8 Data Types

**Numbers**
- Python has three numeric types: `int`, `float`, `complex`.
- Use `type()` to check the data type of any value/variable.
```python
value_1 = 2                 # int
value_2 = 3.5                # float
value_3 = 2 + 3j             # complex
```

**Boolean**
- Represents truth values: `True` and `False`.
```python
value_4 = True
print(type(value_4))   # <class 'bool'>
```

**Strings**
- A sequence of Unicode characters.
- Can be written with single quotes `'...'` or double quotes `"..."` (no functional difference).
- Multi-line strings use triple quotes `'''...'''` or `"""..."""`.

### 1.9 Type Conversion
- Conversion functions: `int()`, `float()`, `str()`, `bool()`, etc.
```python
float(6)     # 6.0
int(100.1)   # 100
str(10)      # '10'
```
- The value being converted must be **compatible** with the target type.
  - `int('20m')` → raises `ValueError` because `'20m'` isn't a valid integer string.
- String concatenation with `+` requires *all* operands to be strings — numbers must first be converted with `str()`.
```python
user = "Anaya"
lines = 200
print("Congratulations, " + user + "! You just wrote " + str(lines) + " lines of code")
```

**Boolean conversion rule (`bool()`):**
- `0` and `""` (empty string) convert to `False`.
- Every other value (including negative numbers, non-zero complex numbers) converts to `True`.

> **AI Example/Explanation:** Python treats "emptiness" or "zero-ness" as False, and everything else as True. So `bool(-4)` is `True` (it's a non-zero number), and `bool("")` is `False` (empty string), but `bool(" ")` (a string with just a space) is `True`, because it isn't *empty* — it has one character in it.

### 1.10 Operators

**Arithmetic Operators**

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition | `5 + 5 = 10` |
| `-` | Subtraction | `5 - 3 = 2` |
| `*` | Multiplication | `8 * 6 = 48` |
| `/` | Division (always returns float) | `3 / 7 = 0.4286` |
| `//` | Floor division (rounds down) | `5 // 5 = 1` |
| `%` | Modulus (remainder) | `5 % 4 = 1` |
| `**` | Exponentiation | `4 ** 3 = 64` |

**Modulus with negative numbers:**
```python
x = -5; y = 4
result = y - (x % y)   # = 1
```
> **AI Example/Explanation:** Python's modulus always returns a result with the *same sign as the divisor*. So `-5 % 4` in Python is `3`, not `-1` (unlike some other languages). This trips up a lot of beginners moving from C/Java.

**Comparison Operators:** `==`, `!=`, `>`, `<`, `>=`, `<=` — each returns a Boolean.

**Assignment Operators:** `=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=` — shorthand for "do the operation, then assign back to the same variable."

**Logical Operators**
- `and`, `or`, `not`.
- **`and` behavior:** evaluates left to right; returns the **first falsy value**, or (if none are falsy) the **last value**.
```python
5 and 0 and "" and 2   # → 0  (first false value)
5 and 19 and 2          # → 2  (all true, so last value)
```
- **`or` behavior:** returns the **first truthy value**, or (if none are truthy) the **last value**.
```python
5 or 0 or "" or 2       # → 5  (first true value)
0 or False or ""        # → ''  (all false, so last value)
```
> **AI Example/Explanation:** Python's `and`/`or` don't just return `True`/`False` — they return one of the *actual values* being compared. Think of `and` as a chain that stops at the first "weak link" (falsy value); `or` stops at the first "strong link" (truthy value). If nothing stops the chain, you get whatever value was last in line.

**Identity Operators:** `is`, `is not` — check whether two variables point to the *same object* in memory (not just equal values).

**Membership Operators:** `in`, `not in` — check whether a value exists inside a sequence (string, list, etc.).

**Ternary (Conditional) Operator:**
```python
result = "Yes" if x > y else "No"
```

**Operator Precedence** (highest to lowest, relevant subset): `()` > `**` > `*`, `/`, `//`, `%` > `+`, `-`
```python
2 + 3 ** 2 * 5
# ** first: 3**2 = 9
# * next:   9*5 = 45
# + last:   2+45 = 47
```

### 1.11 String Multiplication vs Addition
- Strings **can** be multiplied by an integer to repeat them: `"Rim" * 3` → `"RimRimRim"`.
- Strings **cannot** be added directly to numbers — this raises a `TypeError` unless the number is converted with `str()` first.

### 1.12 `None`
- `None` represents "no value" — it is **not** the same as `True` or `False`.
```python
x = None
if x:
    print("True case")
elif x is False:
    print("False case")
else:
    print("None is just None...")
# Output: None is just None...
```

---

## 2. Control Structures

### 2.1 The `if` Statement
- Executes a block of code only if a condition evaluates to `True`.
```python
num = 10
if num > 0:
    print("The number is positive.")
```
- Any non-empty string, non-zero number, or `True` boolean is treated as "truthy" and will satisfy an `if` check on its own (without a comparison operator).
```python
is_raining = True
if is_raining:
    print("Remember to take an umbrella!")
```

### 2.2 The `if-else` Statement
- `else` runs when the `if` condition is `False`.
```python
number = 15
if number % 2 == 0:
    print("The number is even.")
else:
    print("The number is odd.")
```

### 2.3 The `if-elif-else` Chain
- Used to check **multiple conditions sequentially**. Can have multiple `elif` blocks but only one `else` at the end (and `else` is optional).
```python
score = 75
if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("You need to improve.")
```
- **Chained comparisons** are valid in Python: `20 <= temperature <= 30` checks both bounds in one expression.

### 2.4 Nested Conditionals
- An `if` statement can be placed inside another `if` (or `else`) block, allowing you to check a **sub-condition only after an outer condition is true**.
```python
correct_username = "user123"
correct_password = "pass456"
entered_username = input("Enter username: ")
entered_password = input("Enter password: ")

if entered_username == correct_username:
    if entered_password == correct_password:
        print("Login successful!")
    else:
        print("Incorrect password.")
else:
    print("Username not found.")
```

**Leap Year Example (nested conditions):**
```python
year_to_check = int(input("Enter a year to check if it's a leap year: "))
if year_to_check % 4 == 0:
    if year_to_check % 100 != 0 or year_to_check % 400 == 0:
        print(year_to_check, "is a leap year!")
    else:
        print(year_to_check, "is not a leap year.")
else:
    print(year_to_check, "is not a leap year.")
```
> **AI Example/Explanation:** A leap year is divisible by 4, **except** century years (divisible by 100) — unless those are also divisible by 400. So 2000 is a leap year (divisible by 400), but 1900 is not (divisible by 100, not by 400). The nested logic mirrors this exact rule step by step.

### 2.5 Quick Reference — Conceptual Q&A
- `if` executes code when a condition is true.
- `else` executes code when the condition is false.
- `elif` checks multiple conditions sequentially.
- Nested `if` statements execute a block only when **all** the nested conditions are true.
- `if-elif-else` can have multiple `elif` clauses but doesn't require an `else`.

---

## 3. Loops

### 3.1 Iterables
- An **iterable** is any object capable of returning its elements one at a time (e.g., lists, tuples, strings).
```python
Lst = [4, 7, 1, 7, 'A', 'B']
Tpl = (2, 4, 9, 5, 6, 8, 1)
String = "Newton School"
```

### 3.2 Indexing
- Indexing starts from **0**, not 1. To access the *n*th element, use index `n-1`.
```python
My_List = [4, 7, 1, 7, 'A', 'B']
print(My_List[4])   # 5th element → 'A'
```

### 3.3 The `len()` Function
- Returns the number of elements in a list, tuple, or characters in a string.
```python
len(My_List)     # 6
len(My_Tuple)     # 7
len(My_String)    # 13
```

### 3.4 The `range()` Function
- Generates a sequence of numbers. Syntax: `range(start, stop, step)`.
- `stop` is **exclusive** (not included in the output).
```python
list(range(5))          # [0, 1, 2, 3, 4]
list(range(1, 10))       # [1, 2, ..., 9]
list(range(2, 21, 2))    # [2, 4, ..., 20]  (step of 2)
list(range(21, 2, -2))   # [21, 19, ..., 3] (negative step, reverse)
```

### 3.5 Why Use Loops?
- Loops let you repeat an operation over a collection of values *without* writing repetitive code manually.
```python
sales = [1200, 1500, 800, 2000, 1600, 1300, 1700]
total_sales = 0
i = 0
while i < len(sales):
    total_sales += sales[i]
    i += 1
print(f"Total Sales: ${total_sales}")
```

### 3.6 `while` Loop
- Repeats a block **as long as** a condition remains `True`.
```python
step = 1
while step <= 10:
    print(step * 9)   # prints the 9 times table
    step += 1
```
- Can loop based on user input until a specific condition (like typing `'quit'`) is met.
```python
user_input = ''
while user_input != 'quit':
    user_input = input("Enter a word (type 'quit' to exit): ")
    print("You entered:", user_input)
```

### 3.7 `for` Loop
- Iterates directly over the elements of an iterable (list, string, or `range()`).
```python
for i in range(1, 6):
    print(i)
```
- Use `_` as the loop variable when the value itself isn't needed — just the repetition matters.
```python
for _ in range(10):
    print("Newton School")
```
- Can loop directly over list elements:
```python
colors = ['Black', 'Red', 'Grey', 'Blue']
for color in colors:
    print(color)
```

**Factorial with `for`:**
```python
factorial = 1
for num in range(1, 6):
    factorial *= num
print("Factorial of 5:", factorial)   # 120
```

### 3.8 Nested Loops
- A loop placed inside another loop. The inner loop completes fully for each single iteration of the outer loop.

**Multiplication Table:**
```python
for i in range(1, 6):
    for j in range(1, 6):
        print(i * j, end='\t')
    print()
```

**Pattern Printing:**
```python
for i in range(5):
    for j in range(i + 1):
        print('*', end=' ')
    print()
# *
# * *
# * * *
# * * * *
# * * * * *
```

**Pyramid Pattern:**
```python
n = 5
for i in range(n):
    for j in range(n - i - 1):
        print(" ", end="")
    for j in range(2 * i + 1):
        print("*", end="")
    print()
```
> **AI Example/Explanation:** In the pyramid, each row `i` needs `(n-i-1)` leading spaces (fewer as you go down) and `(2*i+1)` stars (an odd, growing count). This is a classic pattern-printing trick: the total width stays constant, but the balance between spaces and stars shifts row by row.

### 3.9 `break` Statement
- Immediately exits the nearest enclosing loop, skipping any remaining iterations.
```python
for i in range(1, 11):
    if i == 5:
        break
    print(i)     # prints 1,2,3,4 then stops
```

**Prime Number Check (using `break` + `else` on `for`):**
```python
for num in range(2, 20):
    for i in range(2, int(num/2) + 1):
        if num % i == 0:
            break
    else:
        print(num, "is a prime number")
```
- **Explanation of the logic:** Since the smallest factor of any number *N* (other than 1) can be checked up to *N/2*, any divisor beyond *N/2* is redundant to check.
- The `else` clause attached to a `for` loop runs **only if the loop completes without hitting a `break`** — this is a distinctive Python feature (`for...else`).

**Password Guessing Game (`for...else`):**
```python
correct_password = "secret"
max_attempts = 3
for attempt in range(1, max_attempts + 1):
    guess = input("Enter the password: ")
    if guess == correct_password:
        print("Congratulations! You guessed the correct password.")
        break
    else:
        print(f"Attempt {attempt} failed.")
else:
    print("You've exceeded the maximum number of attempts. Access denied.")
```
> **AI Example/Explanation:** `for...else` confuses many people because "else" normally implies "otherwise." Here it actually means "run this if the loop was *not* interrupted by `break`." So it's really an "if-no-break" clause — a way to detect that the loop ran to completion.

**`while True` with `break` (infinite loop pattern):**
```python
while True:
    user_input = input("Enter some text (or 'quit' to exit): ")
    if user_input == 'quit':
        print("Exiting program.")
        break
    else:
        print(f"You entered: {user_input}")
```

### 3.10 `continue` Statement
- Skips the **rest of the current iteration** and moves to the next one (does *not* exit the loop entirely, unlike `break`).
```python
for i in range(1, 11):
    if i % 2 == 0:
        continue
    print(i)     # prints only odd numbers 1,3,5,7,9
```

**Combined Example — Skip Negatives, Exit on Command:**
```python
total_sum = 0
while True:
    input_value = input("Enter a number (or 'exit' to end): ")
    if input_value == 'exit':
        break
    number = int(input_value)
    if number < 0:
        continue
    total_sum += number
print(f"The total sum of non-negative numbers is: {total_sum}")
```

> **AI Example/Explanation:** Think of `break` as "leave the building entirely" and `continue` as "skip to the next item on your to-do list without finishing this one." `break` stops the whole loop; `continue` just jumps back to the top of the loop for the next iteration.

---

## 4. Functions

### 4.1 What Is a Function?
- **Definition:** A function is a named block of code that performs a specific task — it can take input, process/manipulate it, and return an output.
- **Why use functions?** Without them, repeating a task (e.g., cooking multiple orders of the same recipe) means duplicating code every time. A function lets you define the logic *once* and reuse it via a simple function call.

> **AI Example/Explanation:** Imagine teaching a robot a recipe. Without a function, you'd have to re-type every single step each time an order comes in — 3 bowls of maggi means writing the recipe 3 times. With a function (`def cook_maggi(): ...`), you teach the robot once, and then just say "make maggi" three times. This is the core value of functions: **write once, use many times.**

### 4.2 Defining and Calling a Function
```python
def cook_maggi():
    print("1 packet of maggie")
    print("250 ml of water")
    print("mix all and cook for 5 minute")
    print("maggi is ready")

cook_maggi()    # calling the function
cook_maggi()    # can call it as many times as needed
```

### 4.3 Function with Return Value vs No Return
- A function with no explicit `return` statement implicitly returns `None`.
```python
def greet(name):
    print(name)

result = greet("Raj")
print(result)    # None, because greet() has no return statement
```
- To get a usable value back from a function, use `return`.
```python
def is_palindrome(number):
    str_num = str(number)
    return str_num == str_num[::-1]
```

### 4.4 Function Arguments — Types

**a) Default Arguments**
- Give a parameter a default value used only when the caller doesn't supply that argument.
```python
def myFunc(x, y=20):
    print("x:", x)
    print("y:", y)

myFunc(10, 30)   # x=10, y=30 (overrides default)
```
- **Rule:** Default-valued parameters must always come *after* non-default parameters in the function signature. Violating this order raises a `SyntaxError`/`IndentationError`.
```python
def myFunc(x, y=20, z=10):   # correct order
    ...
```

**b) Keyword Arguments**
- Pass arguments by explicitly naming the parameter, regardless of order.
```python
def student(firstname, lastname):
    print(firstname, lastname)

student(firstname='Raj', lastname='Kumar')
student(lastname='swaraj', firstname='setty')   # order doesn't matter
```

**c) Positional Arguments**
- Arguments matched to parameters strictly by their **position/order** in the call.
```python
def name_age(name, age):
    print("Hi, I am", name)
    print("My age is", age)

name_age("Gourav", 25)    # correct order → correct output
name_age(25, "Gourav")    # wrong order → wrong/confusing output
```

**d) `*args` — Variable Number of Positional Arguments**
- Collects any number of extra positional arguments into a tuple.
```python
def my_function(*names):
    for name in names:
        print(name)

my_function('Welcome', 'to', 'Newton School')
```
```python
def calculate_average(*numbers):
    total = sum(numbers)
    count = len(numbers)
    print(f"Average: {total/count}")

calculate_average(10, 20, 30, 40)   # Average: 25.0
```

**e) `**kwargs` — Variable Number of Keyword Arguments**
- Collects any number of extra keyword arguments into a dictionary.
```python
def func_keyword_args(**keywords):
    for key, value in keywords.items():
        print("%s == %s" % (key, value))

func_keyword_args(first='All', mid='The', last='Best')
```

> **AI Example/Explanation:** Think of `*args` as a bag that collects any *unnamed* extra items someone hands you (accessed like a list/tuple), and `**kwargs` as a bag that collects any *labeled* extra items (accessed like a dictionary of key-value pairs). Both let a function accept a flexible, unknown number of inputs.

### 4.5 Nested Function Logic — Full Example
```python
def cook_maggi(spice, water):
    default_spice = 2
    default_water = 250
    print("1 packet of maggie")
    if spice > default_spice:
        return "Spicy maggi is ready"
    elif water > default_water:
        return "Soupy maggi is ready"
    else:
        return "Normal maggi is ready"

customer1 = cook_maggi(5, 250)
print(f"{customer1} and served to the customer")
```

### 4.6 Built-in and Common Custom Functions
```python
def calculate_average(numbers):
    return sum(numbers) / len(numbers)   # sum() and len() are built-ins

def find_max(a, b):
    return max(a, b)
```

### 4.7 Lambda (Anonymous) Functions
- A lambda is a small, unnamed, single-expression function defined with the `lambda` keyword.
- Syntax: `lambda arguments: expression`
```python
max_of_two = lambda x, y: x if x > y else y
print(max_of_two(10, 7))   # 10
```
```python
starts_with_letter = lambda word, letter: word.startswith(letter)
print(starts_with_letter("python", "p"))   # True
```

> **AI Example/Explanation:** A lambda is like a function you use once and throw away — instead of writing `def double(x): return x*2` and calling `double(5)`, you can write `lambda x: x*2` inline, right where you need it. It's especially handy as a quick argument to functions like `map()`, `filter()`, and `reduce()`, which expect a function to apply.

### 4.8 `map()` Function
- Applies a given function to **every item** of an iterable and returns a map object (convert to `list()` to view).
```python
numbers = [1, 2, 3, 4, 5]
squared = map(lambda x: x**2, numbers)
print(list(squared))    # [1, 4, 9, 16, 25]
```
```python
words = ["apple", "banana", "cherry"]
lengths = map(len, words)
print(list(lengths))    # [5, 6, 6]
```

### 4.9 `functools.reduce()`
- Applies a function **cumulatively** to the items of an iterable, reducing it to a single value.
```python
import functools
numbers = [1, 2, 3, 4, 5]
sum_of_numbers = functools.reduce(lambda a, b: a + b, numbers)
print(sum_of_numbers)   # 15
```
```python
numbers = [47, 11, 42, 102, 13]
max_number = functools.reduce(lambda a, b: a if a > b else b, numbers)
print(max_number)       # 102
```

> **AI Example/Explanation:** `reduce()` works like folding a strip of paper in half repeatedly until you're left with one small square. It takes the first two elements, combines them per your function, then combines that result with the next element, and so on — until only one final combined value remains.

### 4.10 `filter()` Function
- Creates an iterator containing only the elements of an iterable that satisfy a given condition (function returns `True`).
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)   # [2, 4, 6, 8, 10]
```
```python
strings = ["apple", "", "banana", " ", "cherry", " "]
non_empty_strings = filter(lambda s: s.strip(), strings)
print(list(non_empty_strings))   # ['apple', 'banana', 'cherry']
```

---

## 5. Strings, Lists, and Tuples

### 5.1 Creating Strings
```python
single_line_string1 = "Hello, World!"
single_line_string2 = 'Hello, World!'    # no difference from double quotes
multi_line_string = """This is
a multi-line
string."""
```

### 5.2 String Indexing
```python
a = "Hello"
print(a[0])   # 'H'  (first letter — index 0)
print(a[3])   # 'l'  (fourth letter — index 3)
```

### 5.3 String Concatenation — Multiple Methods
1. **Using `+` operator** — simplest, most direct:
```python
full_greeting = "Hello" + ", " + "World" + "!"
```
2. **Using `join()`** — joins a list/iterable of strings using a separator string:
```python
words = ["Python", "is", "awesome"]
sentence = "01".join(words)   # "Python01is01awesome"
```
3. **Concatenation in a loop:**
```python
numbers = ["one", "two", "three"]
concatenated_string = ""
for number in numbers:
    concatenated_string += number + " "
```

### 5.4 String Slicing
- Syntax: `string[start:end:step]` — `end` is **exclusive**.
```python
a = "Hello, World!"
print(a[1:5])    # 'ello'
```

**Slicing with a Step:**
```python
text = "I am Persuing data science certification from Newton School "
slice3 = text[1:8:2]     # every 2nd character between index 1 and 7
```

**Negative Step (Reversal):**
```python
text = "Hello, World!"
slice4 = text[::-1]      # '!dlroW ,olleH'
```

**Omitting Indices:**
```python
text[:4]    # from the beginning up to (not including) index 4
text[7:]    # from index 7 to the end
```

> **AI Example/Explanation:** Think of slicing syntax `[start:end:step]` as "start here, stop *before* here, and skip this many each time." Omitting `start` means "begin at 0"; omitting `end` means "go to the very end"; a `step` of `-1` walks backward, one character at a time, which is why `text[::-1]` reverses a string.

### 5.5 String Immutability
- Strings **cannot** be modified in place — attempting `name[0] = "U"` raises a `TypeError`.
- You *can* reassign the entire variable to a brand-new string.
```python
name = "Adam Jones"
name = "Jack"    # this creates a new string and reassigns the variable
```

> **AI Example/Explanation:** A string in Python is like a printed page — you can't erase and rewrite a single letter on it, but you *can* throw the page away and print a brand-new one. "Reassigning" a variable to a new string is exactly that: the old string object is discarded and the variable now points to a completely different one.

### 5.6 Common String Methods

| Method | Purpose | Example |
|---|---|---|
| `.upper()` | Converts to uppercase | `"hello".upper()` → `"HELLO"` |
| `.lower()` | Converts to lowercase | `"HELLO".lower()` → `"hello"` |
| `.strip()` | Removes leading/trailing whitespace | `"  hi  ".strip()` → `"hi"` |
| `.split(sep)` | Splits string into a list | `"a,b".split(',')` → `["a","b"]` |
| `.replace(old,new)` | Replaces substring | `"hi world".replace("world","py")` |
| `.find(sub)` | Returns index of first occurrence (or -1) | `"hello world".find("world")` → 6 |
| `.format()` | Substitutes `{}` placeholders | `"num is {}".format(10)` |
| `.startswith(x)` | Checks if string starts with `x` | Returns Boolean |

### 5.7 Escape Sequences
- `\n` — newline character (line break)
- `\t` — horizontal tab

### 5.8 f-Strings and `.format()` — Advanced Usage
```python
name = "Charlie"
age = 28
print(f"My name is {name} and I am {age} years old.")
print(f"In ten years, {name} will be {age + 10} years old.")   # expressions allowed inside {}
```
```python
name = "Bob"; age = 25
"My name is {0} and {1}'s age is {age}.".format(name, "his", age=age)
```
- f-strings support **positional and keyword** substitution simultaneously with `.format()`.

### 5.9 Lists — Mutability
- Lists **are mutable**: their elements can be changed after creation (unlike strings).
```python
my_list = ['H','e','l','l','o']
my_list[1] = 'h'    # allowed — lists can be modified in place
```

### 5.10 List Methods

| Method | Purpose |
|---|---|
| `.append(x)` | Adds `x` to the end of the list |
| `.extend(iterable)` | Appends *each* element of an iterable to the list |
| `.insert(i, x)` | Inserts `x` at index `i` |
| `.remove(x)` | Removes the first occurrence of `x` |
| `.pop([i])` | Removes and returns element at index `i` (or last element if omitted) |
| `.clear()` | Removes all items from the list |
| `.index(x)` | Returns the index of the first occurrence of `x` |
| `.count(x)` | Returns how many times `x` appears |
| `.sort()` | Sorts the list in ascending order (in place) |
| `.reverse()` | Reverses the order of elements (in place) |

```python
todo_list = ["Buy groceries", "Call Mike"]
todo_list.append("Pay bills")   # ['Buy groceries', 'Call Mike', 'Pay bills']

primary_tasks = ["Reply emails", "Prepare report"]
primary_tasks.extend(["Schedule meeting", "Book flight"])

tasks = ["Call Sarah", "Prepare lunch"]
tasks.insert(0, "Finish report")   # inserted at the front

tasks = ["Read book", "Email client", "Attend meeting"]
tasks.remove("Email client")

tasks = ["Order supplies", "Book tickets", "Schedule meeting"]
last_task = tasks.pop()            # removes and returns 'Schedule meeting'
```
> **Note (important distinction):** `.remove(x)` deletes by **value**; `.pop(i)` deletes by **index** and also returns the removed value.

### 5.11 Tuple Methods
- Tuples support only two methods since they are **immutable** (cannot be changed after creation):
  - `.index(x)` — returns the index of the first occurrence of `x`
  - `.count(x)` — returns the number of occurrences of `x`
```python
numbers = (1, 2, 3)
numbers.index(2)   # 1
numbers = (1, 2, 2, 3)
numbers.count(2)   # 2
```

### 5.12 `map()` on Lists — Additional Examples
```python
celsius = [0, 10, 20, 34.5]
fahrenheit = map(lambda x: (9/5) * x + 32, celsius)
print(list(fahrenheit))   # [32.0, 50.0, 68.0, 94.1]
```

### 5.13 List Comprehensions
- **Why use them?**
  - **Concise syntax:** builds a list in a single readable line.
  - **Flexible expressions:** supports `for` and optional `if` clauses for filtering/transforming.
  - **Efficient and readable** for simple tasks (though complex logic may still be clearer as a regular loop).

- Basic syntax: `[expression for item in iterable if condition]`

```python
numbers = [1, 2, 3, 4, 5]
squared_tuples = [(x, x**2) for x in numbers]
# [(1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]

words = ["Hello", "WORLD", "Python", "List"]
lowercase_words = [word.lower() for word in words]
# ['hello', 'world', 'python', 'list']
```

**Nested List Comprehension (flattening a matrix):**
```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
# [1, 2, 3, 4, 5, 6, 7, 8, 9]
```
> **AI Example/Explanation:** Reading a nested comprehension left to right mirrors writing nested `for` loops: `for row in matrix` is the outer loop, `for num in row` is the inner loop, and `num` (at the very front) is what gets collected. It's the same logic as:
> ```python
> flattened = []
> for row in matrix:
>     for num in row:
>         flattened.append(num)
> ```
> just condensed into one line.

---

## 6. Sets and Dictionaries

### 6.1 Sets — Core Properties
- A **set** is an unordered collection of **unique** elements (no duplicates allowed).
- Created using curly braces `{}` or the `set()` function.
```python
my_set = {1, 2, 3}
my_set = set([4, 5, 5, 6])   # duplicates automatically removed → {4, 5, 6}
```

**Real-world use case — Unique Visitor Tracker:**
```python
visitors = ['Alice', 'Bob', 'Alice', 'David', 'Carol', 'Bob']
unique_visitors = set(visitors)   # {'Alice', 'Bob', 'David', 'Carol'}
```

### 6.2 Set Methods
- `.add(x)` — adds an element.
- `.remove(x)` — removes an element; raises `KeyError` if not found.
- `.discard(x)` — removes an element; does **not** raise an error if not found.

```python
my_set = {1, 2, 3, 4}
my_set.remove(4)      # raises error if 4 doesn't exist
my_set.discard(3)     # safe removal, no error even if missing
```

### 6.3 Set Operations

| Operator | Operation | Meaning |
|---|---|---|
| `\|` | Union | All elements from both sets |
| `&` | Intersection | Elements common to both sets |
| `-` | Difference | Elements in the first set but not the second |
| `^` | Symmetric Difference | Elements in either set, but **not** both (excludes common elements) |

```python
a = {1, 2, 3}
b = {3, 4, 5}
a | b   # {1, 2, 3, 4, 5}
a & b   # {3}
a - b   # {1, 2}
a ^ b   # {1, 2, 4, 5}
```

### 6.4 Other Set Operations
```python
len(my_set)              # number of elements
list(my_set)              # convert set → list
tuple(my_set)              # convert set → tuple
```

### 6.5 Set Comprehensions
```python
my_set = {x for x in range(10) if x % 2 == 0}   # {0, 2, 4, 6, 8}

words = ['apple', 'banana', 'zzxt', 'cherry']
vowels = {'a', 'e', 'i', 'o', 'u'}
vowel_words = {word for word in words if any(letter in vowels for letter in word)}
```
- `any()` is a built-in that returns `True` if **at least one** item in an iterable satisfies the condition.

**Practical Set Examples:**
```python
def count_unique_elements(lst):
    return len(set(lst))    # counts distinct elements

def find_common_elements(list1, list2):
    return list(set(list1) & set(list2))    # intersection between two lists
```

### 6.6 Dictionaries — Core Properties
- A **dictionary** stores data as **key-value pairs**. Keys must be unique.
- Created using curly braces `{}` or the `dict()` constructor.
```python
my_dict = {'name': 'Alice', 'age': 25}
my_dict = dict(name='Alice', age=25)
```

### 6.7 Accessing Elements
```python
my_dict = {'name': 'Jack', 'age': 25}
print(my_dict['name'])     # direct key access — raises KeyError if missing
print(my_dict.get("name")) # safer — returns None (or a default) if key doesn't exist
```

**E-commerce Product Catalog Example (Nested Dictionary Access):**
```python
products = {
    1001: {'name': 'T-shirt', 'price': 19.99, 'quantity': 50},
    1002: {'name': 'Jeans', 'price': 39.99, 'quantity': 40}
}
products[1001]['quantity'] -= 1    # updating a nested value
```

### 6.8 Adding and Modifying Elements
```python
my_dict = {'name': 'Alice', 'age': 25}
my_dict['address'] = '123 Street'    # adds a new key
my_dict['age'] = 26                   # modifies an existing key
my_dict.update({'name': 'xyz', 5: 'Spinach'})    # bulk update / add
```

### 6.9 Removing Elements
- `.pop(key)` — removes a key and returns its value.
- `del dict[key]` — removes a key (no return value).
```python
age = my_dict.pop('age')
del my_dict['address']
```

### 6.10 Other Dictionary Operations
```python
len(my_dict)                # number of key-value pairs
'name' in my_dict            # membership check (checks KEYS by default) → True/False
```

### 6.11 Iterating Through a Dictionary
```python
for key in my_dict.keys():       # iterate over keys
    print(key)

for value in my_dict.values():   # iterate over values
    print(value)

for key, value in my_dict.items():  # iterate over key-value pairs
    print(key, value)
```

### 6.12 Copying a Dictionary — Important Caveat
```python
original = {'name': 'Alice', 'age': 25}
copy_dict = original     # NOT a real copy!
```
- Simply assigning `copy_dict = original` does **not** create a new dictionary — both names point to the **same object in memory** (confirmed via `id(copy_dict) == id(original)`). Modifying one modifies the other.

> **AI Example/Explanation:** This is one of the most common beginner traps in Python. `copy_dict = original` doesn't duplicate the dictionary — it's like giving a second nickname to the *same* person. Any change made through either name affects the same underlying dictionary. To make an actual independent copy, use `original.copy()` or `dict(original)` instead.

### 6.13 Dictionary Comprehensions
```python
squares = {x: x*x for x in range(6)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

### 6.14 Nested Dictionaries
- A dictionary can store other dictionaries as values, enabling structured, hierarchical data.
```python
company = {
    "Sales": {
        "Raj": {"ID": 101, "Title": "Sales Manager"},
        "Akash": {"ID": 102, "Title": "Sales Representative"}
    },
    "IT": {
        "Ranveer": {"ID": 201, "Title": "IT Manager"}
    }
}
print(company["Sales"]["Raj"])   # {'ID': 101, 'Title': 'Sales Manager'}
```

### 6.15 Practical Dictionary Patterns

**Word Frequency Counter:**
```python
text = "apple banana apple strawberry banana lemon"
words = text.split()
word_count = {}
for word in words:
    if word in word_count:
        word_count[word] += 1
    else:
        word_count[word] = 1
# {'apple': 2, 'banana': 2, 'strawberry': 1, 'lemon': 1}
```

**Filtering a Dictionary (Comprehension):**
```python
original_dict = {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
filtered_dict = {key: value for key, value in original_dict.items() if value > 2}
# {'c': 3, 'd': 4, 'e': 5}
```

**Grouping Items by Category:**
```python
items = [("apple", "fruit"), ("carrot", "vegetable"), ("banana", "fruit"), ("broccoli", "vegetable")]
category_dict = {}
for item, category in items:
    if category in category_dict:
        category_dict[category].append(item)
    else:
        category_dict[category] = [item]
# {'fruit': ['apple', 'banana'], 'vegetable': ['carrot', 'broccoli']}
```

---

## 7. Recursion

### 7.1 What Is Recursion?
- **Recursion** is a technique where a function **calls itself** to solve a smaller instance of the same problem, until it reaches a base case that can be answered directly.
- Classic analogy: **Russian nesting dolls** — each doll contains a smaller version of itself, until you reach the smallest doll that doesn't open any further (the "base case").

### 7.2 Key Components of a Recursive Function
1. **Base case** — the condition that stops the recursion (prevents infinite recursion).
2. **Recursive case** — where the function calls itself with a smaller/simpler input, moving closer to the base case.

### 7.3 Classic Recursion Examples

**Factorial:**
```python
def factorial(n):
    if n == 0 or n == 1:
        return 1                     # base case
    else:
        return n * factorial(n - 1)  # recursive case

print(factorial(5))   # 120
```

**Fibonacci Sequence:**
```python
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(6))   # 8
```

**Power (Exponentiation):**
```python
def power(base, exp):
    if exp == 0:
        return 1
    else:
        return base * power(base, exp - 1)

print(power(2, 3))   # 8
```

**GCD (Greatest Common Divisor) — Euclidean Algorithm:**
```python
def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)

print(gcd(48, 18))   # 6
```

**Palindrome Check:**
```python
def is_palindrome(s):
    if len(s) < 2:
        return True
    if s[0] != s[-1]:
        return False
    return is_palindrome(s[1:-1])

print(is_palindrome("radar"))   # True
```

**Reverse a String:**
```python
def reverse_string(s):
    if len(s) == 0:
        return s
    else:
        return reverse_string(s[1:]) + s[0]

print(reverse_string("hello"))   # "olleh"
```

**Sum of an Array:**
```python
def sum_array(arr):
    if len(arr) == 0:
        return 0
    else:
        return arr[0] + sum_array(arr[1:])

print(sum_array([1, 2, 3, 4]))   # 10
```

**Tower of Hanoi:**
```python
def tower_of_hanoi(n, source, auxiliary, target):
    if n == 1:
        print(f"Move disk 1 from {source} to {target}")
        return
    tower_of_hanoi(n - 1, source, target, auxiliary)
    print(f"Move disk {n} from {source} to {target}")
    tower_of_hanoi(n - 1, auxiliary, source, target)

tower_of_hanoi(3, 'A', 'B', 'C')
```
> **AI Example/Explanation:** Tower of Hanoi is the "hardest" recursion example here, so let's slow down. The goal: move `n` disks from rod A to rod C, using rod B as a helper, moving only one disk at a time and never placing a bigger disk on a smaller one. The recursive insight is: to move `n` disks from A to C, (1) first move the top `n-1` disks from A to B (using C as helper), (2) move the single largest remaining disk from A to C, (3) then move those `n-1` disks from B to C (using A as helper). Each of steps (1) and (3) is the *same kind of problem*, just smaller — that's why it's naturally recursive.

### 7.4 Recursion vs Iteration (Loops)
- Both can solve repetitive problems, but:
  - **Recursion** breaks a problem into smaller sub-problems of the *same type*, using function calls; it's often more elegant/readable for problems that are naturally recursive (like tree traversal, factorial, Tower of Hanoi).
  - **Iteration (loops)** repeats a block of code using a loop construct (`for`/`while`); it's typically more memory-efficient since it doesn't build up multiple function calls on the call stack.
  - Every recursive function can, in principle, be rewritten as an iterative one, and vice versa — the choice is about readability and problem fit, not capability.

---

## 8. File Handling and Exception Handling

### 8.1 Opening a File
- `open(filename, mode)` opens a file and returns a file object.

**File Modes:**

| Mode | Meaning |
|---|---|
| `'r'` | Read (default) — file must exist |
| `'w'` | Write — creates a new file or **overwrites** an existing one |
| `'a'` | Append — adds to the end of an existing file (creates it if it doesn't exist) |

```python
file = open('example.txt', 'a')   # append mode
file = open('example.txt', 'r')   # read mode
```

### 8.2 Reading Files

**Reading the entire content at once:**
```python
file = open('example.txt', 'r')
content = file.read()
print(content)
file.close()
```

**Reading line by line with `readline()`:**
```python
file = open('example.txt', 'r')
line1 = file.readline()
print(line1, end="")
file.close()
```

### 8.3 Writing and Appending
```python
# Write mode — overwrites existing content
file = open('example.txt', 'w')
file.write("Hello, Python File Handling!")
file.close()

# Append mode — adds to the end without erasing existing content
file = open('example.txt', 'a')
file.write("\nAppending a new line.")
file.close()
```

### 8.4 The `with` Statement (Context Manager)
- Automatically handles closing the file, even if an error occurs — the recommended, safer way to work with files.
```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```

**Reading a file line by line using a loop:**
```python
with open('example.txt', 'r') as file:
    for line in file:
        print(line, end=" ")
```

> **AI Example/Explanation:** Manually calling `file.close()` is risky — if an error happens between `open()` and `close()`, the file might be left open, wasting system resources or even corrupting data. The `with` statement guarantees the file gets closed automatically the moment the block finishes, whether it finished normally or because of an error. It's the Python-recommended way to work with files for exactly this reason.

### 8.5 Exception Handling

**Why it matters:** Errors during runtime (like trying to open a file that doesn't exist, or dividing by zero) will crash a program unless handled — exception handling lets you catch these errors gracefully and keep the program running.

**Core Components:**
1. **`try` block:** Contains code that might raise an exception. If an exception occurs, the rest of the `try` block is skipped, and control moves to `except`.
2. **`except` block:** Handles the exception. You can specify a particular exception type to catch it specifically.
3. **`finally` block:** Always runs, regardless of whether an exception occurred — commonly used for cleanup (like closing a file).
4. **`raise` keyword:** Used to manually trigger an exception when a certain condition in your code is not met.

### 8.6 Exception Handling Examples

**Example 1 — File Not Found:**
```python
try:
    with open("nonexistent.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("Error: The file does not exist.")
```

**Example 2 — File Handling with `finally`:**
```python
try:
    file = open("testfile.txt", "w")
    file.write("Hello World")
except IOError:
    print("Error in writing to the file")
finally:
    file.close()
    print("File closed successfully")
```

**Example 3 — Multiple `except` Clauses:**
- Only the **first matching** `except` clause runs; the rest are ignored.
```python
try:
    num1 = int(input("Enter numerator: "))
    num2 = int(input("Enter denominator: "))
    result = num1 / num2
    with open("nonexistent.txt", "r") as file:
        content = file.read()
except ZeroDivisionError:
    print("Error: Division by zero is not allowed.")
except FileNotFoundError:
    print("Error: The file does not exist.")
```

**Example 4 — `KeyError`:**
```python
my_dict = {'name': 'Alice', 'age': 30}
try:
    print(my_dict['address'])
except KeyError:
    print("Error: Key not found in dictionary.")
finally:
    print("Execution of try-except block is complete.")
```

**Example 5 — `IndexError`:**
```python
my_list = [1, 2, 3]
try:
    element = my_list[5]
except IndexError:
    print("Error: Index is out of range.")
```

**Example 6 — `ValueError`:**
```python
try:
    num = int(input("Enter an integer: "))
except ValueError:
    print("Error: Please enter a valid integer.")
```

> **AI Example/Explanation:** Think of `try/except` like a safety net for a specific kind of accident. A `try` block says "attempt this risky operation." Each `except` clause is a specific plan for a specific kind of failure — a `FileNotFoundError` net catches missing files, a `ZeroDivisionError` net catches math errors, and so on. `finally` is the part that runs *no matter what* — whether the attempt succeeded or failed — much like always turning off the stove after cooking, whether the dish came out right or burnt.

---

## 9. Introduction to OOP

### 9.1 Core Concepts
- **Object-Oriented Programming (OOP)** organizes code around **classes** and **objects**, modeling real-world entities.
- **Class:** A blueprint/template that defines the structure (attributes) and behavior (methods) of a type of object.
- **Object:** A specific instance created from a class, with actual data.

> **AI Example/Explanation:** A class is like an architectural blueprint for a house — it defines what rooms exist and how big they are, but it isn't a house you can live in. An object is an actual house built from that blueprint — you can have many houses (objects) built from the same blueprint (class), each with different paint colors or furniture (different attribute values).

### 9.2 The Constructor (`__init__`)
- The `__init__` method is a special method automatically called when a new object is created from a class. It's used to initialize the object's attributes.
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

my_car = Car("Toyota", "Corolla")
print(f"My car is a {my_car.brand} {my_car.model}")
```

**`self` Keyword:**
- `self` refers to the specific object instance being created/used. It must be the first parameter of any instance method, including `__init__`.

**Constructor with Default Value:**
```python
class Book:
    def __init__(self, title, author="Unknown"):
        self.title = title
        self.author = author

book1 = Book("1984", "George Orwell")
book2 = Book("The Alchemist")   # uses default author "Unknown"
```

**Constructor Performing Calculations:**
```python
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width
        self.area = self.calculate_area()   # calling another method inside __init__

    def calculate_area(self):
        return self.length * self.width

rect = Rectangle(10, 5)
print(f"Area of rectangle: {rect.area}")   # 50
```

### 9.3 Methods
- Functions defined inside a class that operate on the object's data (accessed via `self`).
```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

circle = Circle(5)
print("Area of the circle:", circle.area())   # 78.5
```

### 9.4 Encapsulation
- **Encapsulation** bundles data (attributes) and the methods that operate on that data within a class, and **restricts direct access** to some of an object's components — typically to protect internal state from unintended modification.
- In Python, prefixing an attribute with a **double underscore** (`__`) makes it "private" (name-mangled), meaning it shouldn't be accessed directly from outside the class.

```python
class Account:
    def __init__(self):
        self.__balance = 0    # private variable

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def get_balance(self):
        return self.__balance
```

**Getters and Setters via `@property`:**
```python
class Person:
    def __init__(self, name):
        self.__name = name

    @property
    def name(self):          # getter
        return self.__name

    @name.setter
    def name(self, value):   # setter
        self.__name = value
```

> **AI Example/Explanation:** Encapsulation is like a bank vault: you (external code) can't just reach in and grab the cash (`__balance`) directly — you have to go through the teller window (`deposit()`, `get_balance()`), which enforces rules (like "only positive deposits allowed"). The `@property` decorator is a clean way to let outside code *look* like it's directly accessing an attribute (`person.name`) while secretly routing through controlled getter/setter methods.

### 9.5 Data Abstraction
- **Abstraction** means exposing only the *essential* features of an object while hiding the internal implementation complexity from the user.
- Achieved using **abstract classes** (via Python's `abc` module) and **abstract methods**, which force any subclass to implement specific methods without dictating *how*.

```python
from abc import ABC, abstractmethod

class Shape(ABC):              # abstract class — cannot be instantiated directly
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def area(self, length, width):
        return length * width

myRectangle = Rectangle()
print(myRectangle.area(10, 5))   # 50
```

**Hiding Complexity Example:**
```python
class SmartPhone:
    def make_call(self):
        return "Calling..."

    def __complex_internal_logic(self):   # hidden/private method
        pass

myPhone = SmartPhone()
print(myPhone.make_call())    # user only sees the simple public interface
```

**Interface-like Pattern with Abstract Methods:**
```python
class StorageDevice(ABC):
    @abstractmethod
    def store_data(self, data):
        pass

class HardDrive(StorageDevice):
    def store_data(self, data):
        return "Data stored in Hard Drive"
```

> **AI Example/Explanation:** Abstraction is like using a smartphone — you tap "call," and the phone connects you. You don't need to know (or care) about the cellular signal processing happening underneath. `SmartPhone.make_call()` is the exposed simple interface; `__complex_internal_logic()` is the hidden machinery the user never has to think about.

**Encapsulation vs Abstraction — Key Distinction:**
- **Encapsulation** is about *restricting access* to data (using private variables, getters/setters).
- **Abstraction** is about *hiding implementation complexity* and exposing only what's necessary (using abstract classes/methods).

---

## 10. Inheritance and Polymorphism

### 10.1 What Is Inheritance?
- **Inheritance** allows a class (child/subclass) to acquire the attributes and methods of another class (parent/superclass), promoting code reuse.
```python
class Parent:
    def speak(self):
        print("Parent speaks")

class Child(Parent):     # Child inherits from Parent
    pass

child = Child()
child.speak()    # Output: Parent speaks (inherited, not redefined)
```

### 10.2 The Five Types of Inheritance in Python

**1. Single Inheritance** — one child class inherits from one parent class.
```python
class Animal:
    def __init__(self, name):
        self.name = name
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

pet = Dog("Buddy")
print(pet.speak())   # Woof!
```

**Using `super()` to extend, not just override, a parent method:**
```python
class Employee:
    def __init__(self, name, department):
        self.name = name
        self.department = department
    def show_details(self):
        return f"Employee: {self.name}, Department: {self.department}"

class Manager(Employee):
    def __init__(self, name, department, team_size):
        super().__init__(name, department)   # call parent's __init__
        self.team_size = team_size
    def show_details(self):
        details = super().show_details()      # call parent's method, then extend it
        return f"{details}, Manages {self.team_size} people"

manager = Manager("Alice", "HR", 5)
print(manager.show_details())
# Employee: Alice, Department: HR, Manages 5 people
```

**2. Multiple Inheritance** — a child class inherits from **more than one** parent class.
```python
class Father:
    def gardening(self):
        return "Loves gardening"

class Mother:
    def cooking(self):
        return "Loves cooking"

class Child(Father, Mother):   # inherits from BOTH
    pass

child = Child()
print(child.gardening())   # Loves gardening
print(child.cooking())     # Loves cooking
```

**3. Multilevel Inheritance** — a chain of inheritance across multiple generations (grandparent → parent → child).
```python
class Grandparent:
    def heritage(self):
        return "Family Heritage"

class Parent(Grandparent):    # inherits from Grandparent
    pass

class Child(Parent):          # inherits from Parent (and transitively Grandparent)
    pass

child = Child()
print(child.heritage())   # Family Heritage
```

**4. Hierarchical Inheritance** — **multiple child classes** inherit from a **single parent class**.
```python
class Company:
    def company_policy(self):
        print("Company policy")

class HR(Company):
    pass

class Finance(Company):
    pass

# both HR and Finance separately inherit from Company
```

**5. Hybrid Inheritance** — a combination of two or more types of inheritance in one design (e.g., multiple + multilevel together).
```python
class Grandparent:
    def method_GP(self): return "Method from Grandparent"

class Parent(Grandparent):
    def method_P(self): return "Method from Parent"

class Child(Parent):
    def method_C(self): return "Method from Child"

class OtherParent:
    def method_OP(self): return "Method from OtherParent"

class Grandchild(Child, OtherParent):    # multilevel + multiple combined
    def method_GC(self): return "Method from Grandchild"
```

> **AI Example/Explanation:** Think of these five types visually: **Single** is a straight line (one parent, one child). **Multilevel** is a longer straight line (grandparent → parent → child — an unbroken chain). **Hierarchical** is a tree branching out from one root (one parent, many children). **Multiple** is two lines merging into one point (one child, two parents). **Hybrid** is any combination of the above patterns in a single, more complex family tree.

### 10.3 Method Resolution Order (MRO) with Multiple Inheritance
- When multiple parent classes define the *same* method name, Python resolves which one to use based on the **order the parent classes are listed** in the class definition.
```python
class Father:
    def hobby(self):
        print("Gardening is my hobby")

class Mother:
    def hobby(self):
        print("Painting is my hobby")

class Child(Father, Mother):
    def hobby(self):
        super().hobby()    # resolves to Father's hobby(), since Father is listed first

child = Child()
child.hobby()   # Output: Gardening is my hobby
```

### 10.4 The `super()` Function
- `super()` gives access to methods of a parent class from within a child class — commonly used to:
  - Call the parent's `__init__` to reuse its initialization logic.
  - Extend (rather than completely override) a parent's method.
```python
class Vehicle:
    def start(self):
        print("Vehicle engine started")

class Car(Vehicle):
    def start(self):
        super().start()               # runs parent's version first
        print("Car engine started")   # then adds child-specific behavior

car = Car()
car.start()
# Vehicle engine started
# Car engine started
```

### 10.5 Polymorphism
- **Polymorphism** ("many forms") means the *same* method name can behave differently depending on which object calls it.
```python
class Shape:
    def draw(self):
        pass

class Circle(Shape):
    def draw(self):
        print("Drawing a circle")

class Square(Shape):
    def draw(self):
        print("Drawing a square")

shapes = [Circle(), Square()]
for shape in shapes:
    shape.draw()    # calls the CORRECT draw() for each specific object automatically
```

### 10.6 Ways to Implement Polymorphism

**1. Method Overriding** — a subclass provides its own implementation of a method already defined in its parent class.
```python
class Animal:
    def speak(self):
        return "I'm an animal!"

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"
```

**2. Duck Typing** — Python doesn't require objects to share a common parent class to be treated polymorphically; if an object has the expected method/behavior, it can be used interchangeably ("if it walks like a duck and quacks like a duck...").
```python
class Duck:
    def quack(self):
        return "Quack!"

class Person:
    def quack(self):
        return "I'm pretending to be a duck!"

def make_it_quack(ducklike):
    print(ducklike.quack())

make_it_quack(Duck())     # Quack!
make_it_quack(Person())   # I'm pretending to be a duck!
```
> **AI Example/Explanation:** Duck typing means Python cares about *what an object can do*, not *what class it belongs to*. `make_it_quack()` doesn't check whether its argument is a `Duck` — it just calls `.quack()` on whatever it's given. As long as the object has a `quack()` method, it works, even if the classes are completely unrelated.

**3. Operator Overloading** — redefining how built-in operators (like `+`) behave for custom classes, using special "dunder" (double-underscore) methods.
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):    # defines behavior for the '+' operator
        return Point(self.x + other.x, self.y + other.y)

    def __str__(self):           # defines what print() shows for this object
        return f"Point({self.x}, {self.y})"

point1 = Point(1, 2)
point2 = Point(3, 4)
result = point1 + point2    # calls __add__ automatically
print(result)                # Point(4, 6)
```
> **AI Example/Explanation:** Normally `+` only works on numbers or strings, but `__add__` lets you teach Python what `+` should mean for your *own* custom object. Here, "adding" two `Point` objects means adding their `x` and `y` coordinates separately — Python calls `__add__` behind the scenes whenever you write `point1 + point2`.

---

## Quick Revision Cheat-Sheet

| Topic | Key Takeaway |
|---|---|
| Compiled vs Interpreted | Python is interpreted — runs line by line |
| Variables/Identifiers | Cannot start with digit, no spaces/hyphens, case-sensitive |
| Type Conversion | `int()`, `float()`, `str()` — must be compatible with content |
| `and`/`or` | Return actual values (first falsy / first truthy), not just `True`/`False` |
| `if/elif/else` | Sequential condition checks; only first true branch runs |
| `while` vs `for` | `while` = condition-based; `for` = iterates over a known sequence |
| `break` vs `continue` | `break` exits loop entirely; `continue` skips to next iteration |
| `for...else` | `else` runs only if the loop completes without a `break` |
| Functions | Reusable named blocks; `*args` = extra positional, `**kwargs` = extra keyword |
| Lambda | Anonymous, single-expression function |
| `map`/`filter`/`reduce` | Apply / filter / cumulatively combine values across an iterable |
| Strings | Immutable — indexing/slicing works, but in-place edits raise `TypeError` |
| Lists | Mutable — support `.append()`, `.remove()`, `.sort()`, etc. |
| Tuples | Immutable — only `.index()` and `.count()` methods |
| Sets | Unordered, unique elements; support union/intersection/difference |
| Dictionaries | Key-value pairs; `dict_a = dict_b` does NOT copy — same object reference |
| Recursion | Function calls itself; needs a base case to avoid infinite recursion |
| File Handling | `open()` modes: `'r'` read, `'w'` write/overwrite, `'a'` append; use `with` for auto-close |
| Exception Handling | `try` → risky code, `except` → handle specific error, `finally` → always runs |
| OOP — Class/Object | Class = blueprint, Object = instance |
| Encapsulation | Restrict direct access to data (`__private` attributes, getters/setters) |
| Abstraction | Hide implementation, expose only essentials (`ABC`, `@abstractmethod`) |
| Inheritance | 5 types: Single, Multiple, Multilevel, Hierarchical, Hybrid |
| `super()` | Access parent class methods/constructor from a child class |
| Polymorphism | Same method name, different behavior — via overriding, duck typing, or operator overloading |

