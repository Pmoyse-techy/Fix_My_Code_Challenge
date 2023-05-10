# Fix-My-Code Challenge
A challenge that put to test my ability to **debug** programs written in `python`, `javascript`, `ruby` and `c` programming languages.
###### All scripts had to be made executable

## Mandatory Tasks

### 0. [Fizzbuzz](./0-fizzbuzz.py)
This task required that I debug an implementation of the fizzbuzz program in `python` that never printed `FizzBuzz` but printed only `Fizz` and `Bizz`.
This is what this segment of the original looked liked:
```python
    tmp_result = []
     for i in range(1, n + 1):
         if (i % 3) == 0:
             tmp_result.append("Fizz")
         elif (i % 3) == 0 and (i % 5) == 0:
             tmp_result.append("FizzBuzz")
         elif (i % 5) == 0:
             tmp_result.append("Buzz")
         else:
             tmp_result.append(str(i))
     print(" ".join(tmp_result))
 ```
 Well, you may compare my code to what is displayed here, to see what I figured out was the problem

### 1. [Print Square](./1-print_square.js)
This `javascript` program is supposed to print a square with the character `#` whose size is the number passed to it on the command line (as an argument) when running it, but it had some bug in this particular line of code:
```js
size = parseInt(process.argv[2], 16)
```
The above line of code made the program to print a square of size 15 rather than 10, when 10 was passed as the argument.
Compare this to what I have in my code to see what I changed; if you know what hexadecimals are, read a little about `parseInt` in `javascript` to understand what really happened there.

## Advanced Tasks

### 2. [Sort](./2-sort.rb)
Here, I was required to fix the problem in the `ruby` script.
The script is suppose to sort in an ascending order all integer values passed to it as arguments, on the command line, ignoring non-integer values (string, character, float). Well, I installed `ruby` on my Linux system and added the shebang `#!/usr/bin/env ruby` on line 1, to be able to test the code on my system.
It turned out to be that the bug was in this line of code:
```ruby
result.insert(i - 1, i_arg)
```

The knowledge of `ruby scripts`, `regular expression` and (probably) `bubble sort algorithm` is what you need to understand this task.

### 3. [User password](./3-user.py)
The bug in this file really had to do with the title of the task. A basic knowledge of `python` object oriented programming is actually needed for one to understand this task.

The problem was that: somewhere along the lines of code, the private instance attribute `__password` was rid of its preceding double underscores.
And that was the bug I had to fix

### 4. [Doubly linked list](./4-delete_dnodeint/)
The first thing I did here was to put all the header files in the header file [lists.h](./4-delete_dnodeint/lists.h), so that I only had `#include "lists.h"` in other files. I just like it that way.

The bug here was in the file [delete_dnodeint.c](./4-delete_dnodeint/delete_dnodeint_at_index.c).
It had to do with this lines of code:
```c
else
	{
		(*head)->prev->prev = (*head)->prev;
		free(*head);
		if ((*head)->next)
			(*head)->next->prev = (*head)->prev;
		*head = saved_head;
	}
```

If the index of the node to be deleted is not 0, these 3 things are supposed to happen:
1. The `next pointer` of the node that is before the target node should point the node that is after the target node
2. The target node should be freed or deleted
3. The `prev pointer` of the node that takes the place of the deleted node should point to the node that was before the deleted node.

This sequence of actions will make the node that was before the deleted node to be linked to the node that was after the deleted node.
But the lines of code above do not satisfy that condition, I had to fix the bug.

## Extra Task
### *. [Real Square](./real_square.js)
This was just me playing with [1-print_square.js](./1-print_square.js) to have the square really appear like a square.
I used `console.error()` instead of `process.stderr.write()` and `console.log()` instead of `process.stdout.write()`.
The result when the program is ran, made the name *print square* to make more sense.

#### AUTHOR: [Topman Paul-Dike](https://www.github.com/tpauldike)
