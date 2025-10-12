```python
#!
def sum_even_numbers(numbers):
    even_sum = 0
    for num in numbers:
        if num % 2 == 0:
            even_sum += num
    return even_sum
my_list = [1, 2, 3, 4, 5, 6]
result = sum_even_numbers(my_list)
print("Sum of even numbers:", result)
```

    Sum of even numbers: 12
    


```python
#2
def reverse_string(text):
    return text[::-1]
    
    
```


```python
input_str = "twisha"
reversed_str = reverse_string(input_str)
print("reversed string:",reversed_str)
```

    reversed string: ahsiwt
    


```python
#3
def square_numbers(numbers):
    return [ num ** 2 for num in numbers]
    
```


```python
nums = [1,2,3,4]
squared = square_numbers(nums)
print(squared)
```

    [1, 4, 9, 16]
    


```python
#4
def is_prime(n):
    if n < 2:
        return False  
    for i in range(2, int(n ** 0.5) + 1):  
        if n % i == 0:
            return False
    return True


print("Prime numbers from 1 to 200:")
for num in range(1, 201):
    if is_prime(num):
        print(num, end=" ")
```

    Prime numbers from 1 to 200:
    2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 101 103 107 109 113 127 131 137 139 149 151 157 163 167 173 179 181 191 193 197 199 


```python
#5
def fibonacci_generator(max_terms):
    a,b = 0,1
    for _ in range(max_terms):
        yield a
        a,b = b, a+b

        
        
```


```python
print("fibonacci sequence:")
for num in fibonacci_generator(10):
    print(num, end=" ")
```

    fibonacci sequence:
    0 1 1 2 3 5 8 13 21 34 


```python
#6
def power_of_two_generator(max_exponent):
    for exponent in range(max_exponent + 1):
        yield 2 ** exponent

for value in power_of_two_generator(5):
    print(value)
```

    1
    2
    4
    8
    16
    32
    


```python
#7
def read_file_line_by_line(file_path):
    with open(file_path, 'r') as file:
        for line in file:
            yield line.rstrip('\n')  
```


```python

with open('example.txt', 'w') as f:
    f.write("Line 1: Hello\n")
    f.write("Line 2: World\n")
    f.write("Line 3: From a file\n")
    
for line in read_file_line_by_line('example.txt'):
    print(line)
```

    Line 1: Hello
    Line 2: World
    Line 3: From a file
    


```python
#8
data = [(1, 3), (2, 1), (4, 2)]
sorted_data = sorted(data, key=lambda x: x[1])
print(sorted_data)
```

    [(2, 1), (4, 2), (1, 3)]
    


```python
#9
celsius_temps = [0, 20, 37, 100]
def c_to_f(c):
    return (c * 9/5) + 32
fahrenheit_temps = list(map(c_to_f, celsius_temps))
print("Celsius:", celsius_temps)
print("Fahrenheit:", fahrenheit_temps)
```

    Celsius: [0, 20, 37, 100]
    Fahrenheit: [32.0, 68.0, 98.6, 212.0]
    


```python
#10
text = "Hello, this is twisha."
vowels = 'aeiouAEIOU'

no_vowels = ''.join([ch for ch in text if ch not in vowels])
print("Without vowels:", no_vowels)
```

    Without vowels: Hll, ths s twsh.
    


```python
#11
orders = [
    [34587, 'Learning Python, Mark Lutz', 4, 40.95],
    [98762, 'Programming Python, Mark Lutz', 5, 56.80],
    [77226, 'Head First Python, Paul Barry', 3, 32.95],
    [88112, 'Einführung in Python3, Bernd Klein', 3, 24.99]
]

result = list(map(
    lambda order: (order[0], order[2]*order[3] + 10 if order[2]*order[3] < 100 else order[2]*order[3]),
    orders
))
for item in result:
    print(item)
```

    (34587, 163.8)
    (98762, 284.0)
    (77226, 108.85000000000001)
    (88112, 84.97)
    



---

# 🐍 Python Viva / Practical Questions — Functions, Iterators & Generators

---

## **1️⃣ What is the difference between a function and a method in Python?**

A **function** is a block of code that performs a specific task and can be called independently.  
A **method** is similar but is **associated with an object** and is called using dot notation.

```python
def greet():   # Function
    print("Hello")

text = "hello"
text.upper()   # Method (belongs to string object)


---

2️⃣ Explain the concept of function arguments and parameters in Python.

Parameters are variables defined in a function header.

Arguments are actual values passed to those parameters when the function is called.


def add(a, b):  # a, b = parameters
    return a + b

add(5, 3)       # 5, 3 = arguments


---

3️⃣ What are the different ways to define and call a function in Python?

Functions can be defined using def or lambda.
They can be called directly by name or passed as arguments.

def square(x): 
    return x*x

# Calling the function
print(square(4))

# Using lambda
cube = lambda x: x**3
print(cube(3))


---

4️⃣ What is the purpose of the return statement in a Python function?

The return statement is used to send a value back from a function to the caller.
It also ends the execution of the function.

def add(a, b):
    return a + b


---

5️⃣ What are iterators in Python and how do they differ from iterables?

Iterable: Any object that can return an iterator (like lists, tuples, strings).

Iterator: An object that uses the __next__() method to fetch items one by one.


nums = [1, 2, 3]
it = iter(nums)      # Iterator
print(next(it))      # 1


---

6️⃣ Explain the concept of generators in Python.

Generators are special functions that use the yield keyword instead of return.
They produce values one at a time and maintain their state between calls.

def count_up_to(n):
    for i in range(1, n+1):
        yield i


---

7️⃣ What are the advantages of using generators over regular functions?

Use less memory (values are produced lazily).

Faster for large data sets.

Can handle infinite sequences.

Simplifies code for iterating data streams.



---

8️⃣ What is a lambda function in Python and when is it typically used?

A lambda function is a small anonymous function defined with the lambda keyword.
Used for short, one-line operations like in map(), filter(), etc.

square = lambda x: x**2
print(square(5))


---

9️⃣ Explain the purpose and usage of the map(), reduce(), and filter() functions in Python.

map() → Applies a function to all items in an iterable.

filter() → Filters elements based on a condition.

reduce() → Reduces all elements to a single value using a function.


from functools import reduce
nums = [1, 2, 3, 4]

print(list(map(lambda x: x*2, nums)))       # [2, 4, 6, 8]
print(list(filter(lambda x: x%2==0, nums))) # [2, 4]
print(reduce(lambda x, y: x+y, nums))       # 10


---

🔟 What is the difference between map(), reduce(), and filter() functions in Python?

Function	Purpose	Output

map()	Applies a function to each element	List/iterator of results
filter()	Selects elements that satisfy a condition	Filtered list
reduce()	Combines all elements into one result	Single value



---

