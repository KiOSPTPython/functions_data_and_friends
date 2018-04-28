# Functions, data and friends
## Function definition, signature, arguments and return value

A function can be shortly described as an encapsulated logic of our code. When we want to execute a function, we "call" it. Once a function is called, whatever code we wrote within it is run.

```python
def new_func():
    """This functions prints amazing things to the screen!"""
    x = 10
    y = 2
    print("The function is running!")
    print(f"The secret formula is x*y = {x*y}")


new_func()
>>> The function is running!
>>> The secret formula is x*y = 20
```

The code above shows us the structure we must maintain when we write a function. It begins with the key word `def`, followed by the name of the function along with a pair of parenthesis and a semicolon. The function code beings at the first instance of indentation and ends when the indentation reverts back to the one at the `def` line. In addition, a docstring is written under the function name. This is optional but highly recommended. A summary of what the function does, surrounded by triple double quotes, so others can understand the code at a glance.


When we write functions, we may find ourselves needing something more fluid rather than the same unwavering code executed each time. We can, instead, write dynamic functions that receive an argument or more. These arguments will be available inside the function code as any other variable. Just like we created `x = 10` and `y = 2`, any argument sent will be available for use.

```python
def another_one(name, class_name):
    """Uses the given values to print details about the user."""
    print(f"Hello, {name}!")
    print(f"Welcome to {class_name} class.")

another_one('Frank', 'Linux')
>>> Hello, Frank!
>>> Welcome to Linux class.
```

Once we have a function signature (the statement defining the function and arguments it receives) that uses arguments, if we want to call it we must send those arugments within parenthesis as part of the call.

>Create your own function that receives a name and year of birth. It should print out a welcome message and the century the person was born (1975 -> 1900).


We've previously used functions that may or may not receive an argument, such as `print` and `input`. If we call them with an argument, they work. If we call them without an argument, they work. Magic? Nah, just default arguments.

A default argument can be defined by provindg a default value to the argument in the function signature. This optional argument doesn't have to be sent when we call the function. When the function code uses the argument, it will use the default value we gave it in that case.

```python
def title_print(message='', length=80):
    """Encapsulates a message with some borders"""
    print('-'*length)
    print(f'{message}')
    print('-'*length)

>>> title_print("Default length of a terminal.")
################################################################################
Default length of a terminal.
################################################################################
```

>Create a function that receives height and length of a rectangle. It should print a rectangle with those metrics or a 4x4 one, if none were given.

One other tool we can use in the world of functions is keyword arguments. This means calling a function and specifying the argument names when sending them. This clarifies the code and eases maintenance.
```python
>>> title_print(length=5, message="We repeat, this is only a test. This is only a test.")
#####
We repeat, this is only a test. This is only a test.
#####
```

Notice that when using keyword arguments, their order isn't import. But, they must come after any positional keyword arguments. If we use a keyword argument and provide a positional after it, we'll get an error.
```python
>>> title_print(message="Brace brace!", 10)
SyntaxError: positional argument follows keyword argument
```

>Create a function that prints a pyramid of a given height using a given symbol. Use keyword arguments.


The last thing we need to address is return values. When we used the statement `name = input("Name? ")`, we employed the return value of `input`. A return value of a function is somewhat like the output or result of its operation. And this value can be used anywhere in the code. The function call statement in the code can be considered to be replaced, at runtime, with the value that the function returns. For example, instead of assigning the return value of `input` to a variable, we could've used it directly like so
```python
y = 5 + int(input("Number? "))
```
In this example, input will return a string which we then convert to an int before adding it to 5 and assigning the total to `y`.


For a function to return a value other than None, the default, we must use the `return` statement. When this statement is issued, the function ends and the code continues from where the function was called. 

```python
def persona(age):
    """Returns wether the person is a baby, child, teen or adult."""
    if age < 4:
        return "Baby"
    elif age < 12:
        return "Child"
    elif age < 18:
        return "Teen"
    else:
        return "Adult"

first = persona(15)
second = persona(71)
print(f"Mr First, you are a[n] {first}.")
print(f"Mr Second, you are a[n] {second}.")
>>> Mr First, you are a[n] Teen.
>>> Mr Second, you are a[n] Adult.
```

>Write a function that takes a person's age and returns in which school year they're expected to be. For example, a 13 year old should be in 7th grade. Ages outside a school range should receive an interesting title.

## Basic data structures
The right data structure can help shape code into a readable and efficient one. Other than holding strings and numbers in variables, there are a few more data types that help us manage the items we work with. Some of the most useful ones are list, dict and set.


Lists are a group of items, plain and simple. Imagine you wish to hold a record of a few IP addresses that you're working with. A couple can be handled under the umbrella of some string variables. But, that quickly becomes tedious and down right impossible, if dealing with many IPS. Instead, we can use a variable of type list that allows us to store multiple items. These items can be of any type. In other words, a list can store a combination of integers, strings, other lists, dicts etc. It doesn't have to be of the same type.

```python
ips = ['127.0.0.1', '8.8.4.4', '8.8.8.8', '1.1.1.1']
```

A few common operations we'd like to do on lists is access an item, add or remove one.

```python
>>> print(ips[0])
127.0.0.1
>>> ips.append('localhost')
>>> print(ips)
['127.0.0.1', '8.8.4.4', '8.8.8.8', '1.1.1.1', 'localhost']
>>> ips.remove('127.0.0.1')
>>> print(ips)
['8.8.4.4', '8.8.8.8', '1.1.1.1', 'localhost']
```

With square brackets, we can indicate which item we want to access, using its index number. Indexing starts at 0. So, `ips[0]` will provide us with the first item in the list, `ips[4]` will raise an error but `ips[2]` will not. The append method of a list will add an item to its end while the remove method will remove the first instance of the value given.

>Ask the user to input 3 IP addresses and one number. Store them all in a list variable.


Dicts are another highly useful data structure where a group of items are stored but accessing them is done using a paired key. We insert key: value pairs into the dict and access the value by that key. Imagine accessing a person's details according to his/her ID number.

```python
>>> persons = {5: 'Gabe', 'hello': 'Nature'}
>>> persons['tree'] = 20
>>> print(persons[5])
Gabe
>>> print(persons['tree'])
20
```

The advantage is that this data structure makes readability much easier. We can imply intention and meaning through the code without another fully understanding it. Any (almost) data type can be a key and any data type can be a value. In the above example we used the number 5 as a key for 'Gabe' and the string 'tree' as a new key: value pair in the dict with a value of 20.

>Ask the user to enter 2 persons' ID numbers and name. Store these names in a dict using the IDs as each person's key.
>Ask the user for 2 persons' ID, name, city and age. Store in a new dict, according to ID as key, each person's detail in ANOTHER dict within that dict. This means each key will point to a dict itself.


Another worthy data type is `set`. It holds unique items. In other words, it is close to a list in the sense that it holds items. But, it will not hold repeated values. For example, I can add the first few natural numbers but cannot add 1 a second time.

```python
>>> grocery = {'banana', 'apple', 'strawberry', 'onion'}
>>> print(grocery)
{'banana', 'apple', 'strawberry', 'onion'}

>>> naturals = {1, 2, 3, 1, 2, 3}
>>> print(naturals)
{1, 2, 3}
>>> naturals.add(4)
>>> print(naturals)
{1, 2, 3, 4}
>>> naturals.remove(1)
>>> print(naturals)
{2, 3, 4}
```

Here, we defined a couple of sets. The first is a pleasant list of groceries while the second is a set of natural numbers. In the second set, we can see that any repeated value wasn't added to the set. We can add values to an existing set and remove them. The behavior remains the same.

>Ask the user to input 3 domain names and ensure none were repeated using a set.

## Loops
Loops allow us to easily perform an action multiple times. The basic form of loop is a `while` loop which checks a condition each time it tries to start another cycle of the loop. It will only end looping once the condition is no longer met. The second, more popular, form of loop is the `for` loop. The `for` loop allows us to easily go through an array of items. Mostly it is because experience showed this is the most popular loop usecase among programmers. 

```python
students = ['Josh', 'David', 'Michael', 'Lucy', 'Dora']
i = 0
max_i = len(students)

while i < max_i:
    student = students[i]
    message = f”Welcome to class, {student}.”
    message2 = “Please, take your seat.”
    print(message)
    print(message2)
    i = i + 1
```
In the above example, we used a list of student names and looped through them using the `while` loop. The idea behind this loop is to use an index both for the condition and accessing the list items. This way, once i reaches the number of students (minus one) in the list of students, the loop will end.

>Can you think of a way to split this code into a loop and a function?

```python
students = ['Josh', 'David', 'Michael', 'Lucy', 'Dora']

for student in students:
    message = f”Welcome to class, {student}.”
    message2 = “Please, take your seat.”
    print(message)
    print(message2)
```
This example showcases the `for` loop used to iterate through the same list of students we had before. This time, though, we don't manage the access to the list. The `for` loop does this for us and, each iteration, puts the value of the item in the variable student (which is available after the loop, too). In each iteration, inside the code block, we used the value of student to dynamically print the same message for all students.

>What is the value of `student` after the loop finishes? 
>Write a function that appends a given IP to "attacking" before printing it. Ask the user to provide you with 3 IP addresses, store them in a list and send them, each, to the function using the `for` loop.

Another thought pattern that uses `for` loops, for example, is one where we define actions we want to take. Imagine that each item in the list isn't a basic type like an integer or string but a function. We store a group of functions and call, each of them in the body of the `for` loop.

```python
def syn_flood(ip):
    """Floods the ip given with TCP SYN packets."""
    print(f"Christmas is early, {ip}.")

def ntp_dos(ip):
    """Amplifies our volume using NTP and sends the response to a given IP."""
    print(f"The time is always now, {ip}.")

def memcache_dos(ip):
    """Amplifies our volume using a memcache server and sends the result to a given IP."""
    print(f"Cache this, {ip}.")

attacks = [syn_flood, ntp_dos, slowloris]
for attack in attacks:
    attack('127.0.0.1')
```
Recall that anything in Python is an object that can be referenced. All we did was not store strings/integers but actual functions. Then, we used them like we did until now.

>Find 3 DoS attack types, create a dummy function for each, store them all in a list and call them using `for`.

## List comprehension
A popular shorthand way to define a list is called "list comprehension". We combine `for` and square brackets to define the items we have in our list. Let's look at a few examples.

```python
>>> my_list = [i for i in range(5)]
>>> print(my_list)
[0, 1, 2, 3, 4]
```
What we did here is iterate over the values `range(5)` gives us and made a new list of it.

```python
>>> my_list = [i*10 for i in range(5)]
>>> print(my_list)
[0, 10, 20, 30, 40]
```
This time, we asked for each item that `range(5)` yields us be multiplied by 10 before being stored as an item in `my_list`.

```python
>>> students = ['Josh', 'David', 'Michael', 'Lucy', 'Dora']
>>> hello_students = [f"Hello, {student}" for student in students]
>>> print(hello_students)
['Hello, Josh', 'Hello, David', 'Hello, Michael', 'Hello, Lucy', 'Hello, Dora']
```
Here, we prefixed each student with a string.

```python
def power10(x):
    """Raises a given number to the power of 10."""
    return x**10

>>> powered = [power10(i) for i in range(4)]
>>> print(powered)
[0, 1, 1024, 59049]
```
In this example, we employed a function call within the list comprehention.

```python
>>> powered = [power10(i) for i in range(4) if i > 1]
>>> print(powered)
[1024, 59049]
```
Lastly, we show that conditions also work in list comprehension.

>Use list comprehension to extract the digits from "Peterovich was 11 in 1997". Recall that strings are iterable and str.isdigit returns True if a given string can be a number.


Using list comprehension is powerful but, can also be dangerous. Please, note that using complex statements become unreadable quickly. 
```python
>>> print([[i*j for j in range(11)] for i in range(11)])
[[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
 [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
 [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20],
 [0, 3, 6, 9, 12, 15, 18, 21, 24, 27, 30],
 [0, 4, 8, 12, 16, 20, 24, 28, 32, 36, 40],
 [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50],
 [0, 6, 12, 18, 24, 30, 36, 42, 48, 54, 60],
 [0, 7, 14, 21, 28, 35, 42, 49, 56, 63, 70],
 [0, 8, 16, 24, 32, 40, 48, 56, 64, 72, 80],
 [0, 9, 18, 27, 36, 45, 54, 63, 72, 81, 90],
 [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100]]
```
Consider the above table of multiplication. Works but is easily hard to read.

## Mutable and immutable
An important data type property is wether or not it can be changed - Is it mutable or immutable. When we talk about lists, dictionaries and sets, we talk about mutable data types. After we've given them a value, we can change it without creating a new variable. On the other hand, immutable types cannot be changed "in place". Strings and integers are immutable, for example. Once we have the number 1 in our hands, we cannot change something about it. The only option we have to use another number is to define a new variable with that new number. And, although we don't do this explicitly `x = 1; x = 2` (where is the new variable?), Pythong does it for us, to put it simply.

```python
def add_student(student_list, student_name):
    """Adds a new student to the list of students or replaces one, if over 5"""
    if len(student_list) >= 5:
        student_list.pop()
        student_list.insert(0, student_name)
    else:
        student_list.insert(0, student_name)

>>> students = ['Josh', 'David', 'Michael', 'Lucy', 'Dora']
>>> print(students)
['Josh', 'David', 'Michael', 'Lucy', 'Dora']
>>> add_student(students, 'Davidson')
>>> print(students)
['Davidson', 'Josh', 'David', 'Michael', 'Lucy']
``` 
Although we defined our variable, `students`, outside the function `add_student`, the function was still able to change it from within. This is how a mutable variable behaves. We don't pass it by value, like we do with strings/integers, but we pass it by reference. Once we pass something by reference to a function, the change on that variable in that function will be reflected anywhere else that variable is used.

```python
def time_machine(current_year, destination):
    """This time machine will change the current date!"""
    if current_year != destination:
        print("When this baby hits 88 miles per hour...")
        current_year = destination

>>> today = 2018
>>> back_to = 2015
>>> print(f"We're flying out of {today} and going to {back_to}!")
We're flying out of 2018 and going to 2015!
>>> time_machine(today, back_to)
>>> print(f"What year is this? {today}")
What year is this? 2018
```
In this example, we foolishly try to replicate a famous experiment and fail. The immutable integer is passed by value to the function. When the function changes that variable, it only does it for its own scope. The change on the integer, passed by value, isn't reflected outside the scope of the function. Instead, what happens, is the function creates a new variable.

>Copy paste this code and run it. Just like every other programmer.

Mind? Blown.
>Create a function with a default argument as a list. Append an item to the list inside the function and print the list. Call the function a few times with no arguments. Gotcha.

## Finals
Do you want to play a game? Let's build a Tic Tac Toe game. The rules of the game are straight forward. The user plays against the computer and, each turn, the user/computer choose where to place their mark. Once there's 3 in a row of the same mark, one of them wins. The important part is splitting the game into small tasks as functions and then using them to create the game.


Below is a template you can use to write the game. Feel free to start from scratch or change it. 
```python
from random import choice, randint
# r = randint(2, 7)
# Will randomly choose a number between 2 and 7
# c = choice([4, 3, 7, 1])
# Will randomly choose one of the numbers from the list


PLAYER = 'x'
COMP = '0'
BOARD = """----------------------------
|   {0}    |   {1}    |   {2}    |
|  {0} {0}   |  {1} {1}   |  {2} {2}   |
|   {0}    |   {1}    |   {2}    |
----------------------------
|   {3}    |   {4}    |   {5}    |
|  {3} {3}   |  {4} {4}   |  {5} {5}   |
|   {3}    |   {4}    |   {5}    |
----------------------------
|   {6}    |   {7}    |   {8}    |
|  {6} {6}   |  {7} {7}   |  {8} {8}   |
|   {6}    |   {7}    |   {8}    |
----------------------------"""


def display_board(status):
    """Fills up a board template with symbols according to status."""
    # The *list notation here will send all its items as arg, e.g. format('x', '0', ' ', 'x', ...)
    # This is instead of explicitly writing format(status[0], status[1], status[2], ...)
    print(BOARD.format(*status))


def player_move(status):
    

def computer_move(status):
    

def winner(symbol):
    

def win_3(sequence):
    

def game_end(status):
    

def play():
    """Starts the game!"""
    status = [' ']*9
    display_board(status)
    

play()
```