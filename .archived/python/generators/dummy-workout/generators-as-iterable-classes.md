---
author: catalin

levels:

  - basic

  - medium

type: normal

category: how to

notes: >+
  The line:
    cur = low
  gives error. Should be:
    cur = a
  Also, the generator can be made a bit shorter and more idiomatic Python by
  using a for loop instead of the while loop. Changes made.

  Also, lower_case_with_underscores is mostly preferred for identifier names in
  Python, instead of CamelCase as in, say, Java. Initial capital letter is
  preferred for class names.


links:

  - >-
    [stackoverflow.com](http://stackoverflow.com/questions/19151/how-to-make-class-iterable){website}

---
# Generators as Iterable Classes

---
## Content

Generators are mainly used instead of **iterable classes** because they make the logic and syntax way more human-readable and easier to understand.

 They auto generate the methods `__iter__()` and `__next__()` (`next()` in **Python 2**).

The former returns the iterator object and is implicitly called at the start of iteration, while `next` returns the next values and is called at every iteration.

Consider this generator:
```python
def my_generator(a, b):
    for cur in range(a, b + 1):
        yield cur

mg = my_generator(1, 5)
# Iterate over the generator and
# gets all its items in a list.
print(list(mg))
# [1, 2, 3, 4, 5]
```

It can be also implemented as a class by defining the methods talked about above:
```python
class MyGeneratorClass:
    def __init__(self, a, b):
        self.cur = a
        self.b = b

    def __iter__(self):
        return self

    def __next__(self): 
        if self.cur > self.b:
            raise StopIteration
        else:
            self.cur += 1
            return self.cur - 1

mg2 = MyGeneratorClass(1, 5)
print(list(mg2))
# [1, 2, 3, 4, 5]
```

---
## Practice

Complete the code snippet below such that it makes sense:
```
def my_gen(a, b):
   for cur ?? range(a, b+1):
      ??? cur
mg = my_gen(1, 5)
print(list(mg))
#[1, 2, 3, 4, 5]
```

* yield
* in
* stop
* await
* is
* gen

---
## Revision

What of the following methods are auto generated by generators in Python 2?

???

* next()
* __next__()
* __init__()
* none
* __next__() and next()