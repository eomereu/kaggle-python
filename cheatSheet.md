## Hello, Python

- `type(var)` returns the type of *var*

- Order of operations: **PEMDAS** - **P**arentheses, **E**xponents, **M**ultiplication/**D**ivision, **A**ddition/**S**ubtraction.

- `min(1, 2, 3)` returns minimum of the arguments

- `max(1, 2, 3)` returns maximum of the arguments

- `abs(-2)` returns absolute value

- Some type convertion:
    ```python
    float(10)
    int(3.33)
    int('807') + 1
    ```

- To simply swap values:
    ```python
    a = [1, 2, 3]
    b = [4, 5, 6]
    a, b = b, a 
    ```

## Functions and Getting Help

- `help()` function returns us how and what for we can use a given function:
    ```python
    help(abs) #correct use
    help(abs(-1)) #mistaken use
    ```
    Python evaluates an expression like this from the inside out. First it calculates the value of abs(-2), then it provides help on the output of that expression.
    
- `print()` may have a couple of optional arguments. Two useful ones are: `sep=' '` and `end='\n'` *(default values are as shown)*. `sep` puts that specified character/input between every word of our input. `end` puts it to the end:
    ```python
    print(1, 2, 3, sep=' < ')
    ```
    1 < 2 < 3

- Defining a function:
    ```python
    def least_difference(a, b, c):
        diff1 = abs(a - b)
        diff2 = abs(b - c)
        diff3 = abs(a - c)
        return min(diff1, diff2, diff3)
    ```
    
- When we define a function, we can provide a description to be shown when `help` is used on our function, called as `docstring`. To be used within the above function *least_difference*:
    ```python
    """Return the smallest difference between any two numbers
    among a, b and c.
    
    >>> least_difference(1, 5, -5)
    4
    """
    ```
    The docstring is a triple-quoted string (which may span multiple lines) that comes immediately after the header of a function. When we call `help()` on a function, it shows the docstring.
    
- We can define a default function for a value of an argument like `def func(arg=val)`:
    ```python
    def greet(who="Colin"):
        print("Hello,", who)
    
    greet()
    greet(who="Kaggle")
    # (In this case, we don't need to specify the name of the argument, because it's unambiguous.)
    greet("world")
    ```
    Hello, Colin<br>
    Hello, Kaggle<br>
    Hello, world<br>
    
- Functions that operate on other functions are called *"Higher order functions."*

- By default, `max` returns the largest of its arguments. But if we pass in a function using the optional `key` argument, it returns the argument x that maximizes `key(x)` (aka the 'argmax'):
    ```python
    def mod_5(x):
        """Return the remainder of x after dividing by 5"""
        return x % 5

    print(
        'Which number is biggest?',
        max(100, 51, 14),
        'Which number is the biggest modulo 5?',
        max(100, 51, 14, key=mod_5),
        sep='\n',
    )
    ```
    Which number is biggest?<br>
    100<br>
    Which number is the biggest modulo 5?<br>
    14