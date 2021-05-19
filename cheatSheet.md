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
    Hello, Colin  
    Hello, Kaggle  
    Hello, world  
    
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
    Which number is biggest?  
    100  
    Which number is the biggest modulo 5?  
    14
    
- `pass` is a keyword that does literally nothing. We use it as a placeholder because after we begin a code block, Python requires at least one line of code

- `round(num,ndigits)` ndigits sets the number of digits after the dot to be shown. May also be set to negative. If set as -1 then rounds to nearest 10, if set to -1 then rounds to nearest 100 and so on.

## Booleans and Conditionals

- `and` is evaluated before `or`.

- We can also split it over multiple lines to emphasize the 3-part structure:
    ```python
    prepared_for_weather = (
        have_umbrella 
        or ((rain_level < 5) and have_hood) 
        or (not (rain_level > 0 and is_workday))
    )
    ```

- `if` - `elif` - `else`

- As `int()` was turning things into integer, `bool()` function turns things into boolean:
    ```python
    print(bool(1)) # all numbers are treated as true, except 0
    print(bool(0))
    print(bool("asf")) # all strings are treated as true, except the empty string ""
    print(bool(""))
    # Generally empty sequences (strings, lists, and other types lists and tuples) are "falsey" and the rest are "truthy"
    ```
    True  
    False  
    True  
    False

- So we can use non-boolean objects in if conditions:
    ```python
    if 0:
        print(0)
    elif "spam":
        print("spam")
    ```
    spam

- Ternary operator: A more compct version of a conditional:
    ```python
    if total_candies == 1:
        print("Splitting 1 candy")
    else:
        print("Splitting", total_candies, "candies")
    ```
    ```python
    print("Splitting", total_candies, "candy" if total_candies == 1 else "candies")
    ```

- Another point of view:
    ```python
    def concise_is_negative(number):
        return number < 0
    ```

- `int()` on boolean values will return 1 if bool is True, will return 0 if bool is False. *Just by doing addition with booleans, Python implicitly does the integer conversion.*
    ```python
    int(bool(True))
    int(bool(False))
    True + False + True
    ```
    1  
    0  
    2

- Return whether the customer wants exactly one of the three available toppings on their hot dog:  
    ```python
    def exactly_one_topping(ketchup, mustard, onion):
        return True if int(ketchup) + int(mustard) + int(onion) == 1 else False
    ```
    More compact way:
    ```python
    def exactly_one_topping(ketchup, mustard, onion):
        return (int(ketchup) + int(mustard) + int(onion)) == 1
    ```
    Fun fact: we don't technically need to call `int` on the arguments. Just by doing addition with booleans, Python implicitly does the integer conversion. So we could also write:
    ```python
    def exactly_one_topping(ketchup, mustard, onion):
        return (ketchup + mustard + onion) == 1
    ```


## Lists
Created  within square brackets `[]` and they are mutable/modifiable.
- Elements at the end of the list can be accessed with negative numbers, starting from -1:
    ```python
    planets[-1]
    ```
    'Neptune'
    ```python
    planets[-2]
    ```
    'Uranus'

- Slicing: Following corresponds to [0,3)
    ```python
    planets[0:3]
    ```
    ['Mercury', 'Venus', 'Earth']  

    The starting and ending indices are both optional. If we leave out the start index, it's assumed to be 0.
    ```python
    planets[:3]
    ```
    ['Mercury', 'Venus', 'Earth']  

    Following code gives all the planets from index 3 onward:
    ```python
    planets[3:]
    ```
    ['Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']  

    We can also use negative indices when slicing:
    ```python
    # All the planets except the first and last
    planets[1:-1]
    ```
    ['Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus']  
    ```python
    # The last 3 planets
    planets[-3:]
    ```
    ['Saturn', 'Uranus', 'Neptune']

- Changing lists:
    ```python
    planets[:3] = ['Mur', 'Vee', 'Ur']
    ```

- `len(list)` returns the length of a list.

- `sorted(list)` returns a sorted version of a list.

- `sum(list)` returns summation of the elements in a list.

- **Everything** in Python is an object. Objects carry some things which we can access that stuff using *dot* syntax around with them.

- `num.imag` For example, numbers in Python carry around an associated variable called `.imag` representing their imaginary part:
    ```python
    x = 12
    # x is a real number, so its imaginary part is 0.
    print(x.imag)
    # Here's how to make a complex number, in case you've ever been curious:
    c = 12 + 3j
    print(c.imag)
    ```
    0  
    3.0

- The things an object carries around can also include functions. A function attached to an object is called a **method**. Non-function things attached to an object, such as `.imag`, are called **attributes**.

- `num.bit_length()` returns the number of bits necessary to represent self in binary.

- We can also pass in methods into `help`, *But without parantheses*:
    ```python
    help(num.bit_length)
    ```

### List Methods
- `.append(object)` modifies a list by adding *object* to the end

- `.pop()` removes and returns the last element of a list

- `.pop(index)` removes and returns the element of a list with given index

- `.remove(val)` removes first occurence of value. Raises `ValueError` if *val* is not in the list

- `.index(val)` returns the index of given *val*. Raises `ValueError` if *val* is not in the list

- `object in list` returns if *object* exists in list or not as True/False

- `.clear()` removes all objects from list

- `.count(val)` returns number of occurences of *val* in the list

- `.insert(index, object)` inserts *object* before *index*

- `.reverse()` reverses the list ***\*in place\****

- `.sort()` sorts the list ***\*in place\****

### Tuples
Created within parantheses `()` or simply without any parantheses etc. and they are immutable/unmodifiable
```python
t = (1, 2, 3)
# or
u = 1, 2, 3
```
- Multiple return values can be individually assigned:
    ```python
    x = 0.125
    x.as_integer_ratio()
    ```
    (1, 8)  

    ```python
    numerator, denominator = x.as_integer_ratio()
    print(numerator / denominator)
    ```
    0.125

## Loops and List Comprehensions
- `print(end=' ')` sets a special character for the ending:
    ```python
    a = [1, 2, 3]
    for num in a:
        print(num)
        print(num, end=' ')
    ```
    1  
    2  
    3  
    1 2 3

- We can even iterate over characters of a string:
    ```python
    s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
    msg = ''
    # print all the uppercase letters in s, one at a time
    for char in s:
        if char.isupper():
            print(char, end='') 
    ```
    HELLO

- `char.isupper()` returns `True` if the character is uppercase, `False` otherwise.

- `range()` returns a sequence of numbers:
    ```python
    for i in range(3):
        print(i, end=' ')
    ```
    0 1 2

### List Comprehensions
An example case of *list comprehension*
```python
squares = [n**2 for n in range(10)]
squares
```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]  

Here's how we would do the same thing without a list comprehension:
```python
squares = []
for n in range(10):
    squares.append(n**2)
squares
```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]  

We can also add an `if` condition:
```python
short_planets = [planet for planet in planets if len(planet) < 6]
short_planets
```
Here's an example of filtering with an `if` condition and applying some transformation to the loop variable:
```python
# str.upper() returns an all-caps version of a string
loud_short_planets = [planet.upper() + '!' for planet in planets if len(planet) < 6]
loud_short_planets
```
['VENUS!', 'EARTH!', 'MARS!']  

Another example of *list comprehension* vs conventional solution:
```python
def count_negatives(nums):
    """Return the number of negative numbers in the given list.
    
    >>> count_negatives([5, -1, -2, 0, 3])
    2
    """
    n_negative = 0
    for num in nums:
        if num < 0:
            n_negative = n_negative + 1
    return n_negative
```
Solution with *list comprehension*:
```python
def count_negatives(nums):
    return len([num for num in nums if num < 0])
```

- `any([if_condition for item in list])` returns `True` if the condition counts for even a single item, `False` otherwise:
    ```python
    def has_lucky_number(nums):
        return any([num % 7 == 0 for num in nums])
    ```
Some examples:
```python
def elementwise_greater_than(L, thresh):
    """Return a list with the same length as L, where the value at index i is 
    True if L[i] is greater than thresh, and False otherwise.
    
    >>> elementwise_greater_than([1, 2, 3, 4], 2)
    [False, False, True, True]
    """
    return [i > thresh for i in L]
```
```python
def menu_is_boring(meals):
    """Given a list of meals served over some period of time, return True if the
    same meal has ever been served two days in a row, and False otherwise.
    """
    return any([meals[i] == meals[i-1] for i in range(1,len(meals))])
```