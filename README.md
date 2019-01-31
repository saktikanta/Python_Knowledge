# Python class and type
### Python classes are all types.

Type is nothing but called template of an object.

The builtin calsses have their own types.

User-defined classes can inharite their types
from the builtin classes or the generic type.

The type function can display the type of an object and can also used to define a new type.

Where the class statement is typically used to define a new type.

Typically the type function is not used to create classes,
instead we use class statement to do so.


### Type function used to display the type
```python
print('The type of 1 is:', type(1))
print('The type of [] is:', type([]))
```
result:
```pyton
The type of 1 is: <class 'int'>
The type of [] is: <class 'list'>
```
### Type function used to define a type
below is the basic defination of type
```python
a_class = type('a_class',(),{}) 
print('The type of a_type is: ', type(a_class))
an_inst = a_class()
print('The type of an_inst is: ', type(an_inst))
```
result:
```pyton
The type of a_type is:  <class 'type'>
The type of an_inst is:  <class '__main__.a_class'>
```

### Below is the type defination with attributes
```python
a_type=type('a_type',(),{'start':1,'a_method':
             lambda self: 'This is an instance of ' +
             str(self.__class__)})
type_inst = a_type()
print('The type of a_type is: ', type(a_type))
print('The type of type_inst is: ', type(type_inst))
print('Class variable type_inst.start is:', type_inst.start)
print('Calling type_inst.a_method() returns:', type_inst.a_method())
```
result:
```pyton
The type of a_type is:  <class 'type'>
The type of type_inst is:  <class '__main__.a_type'>
Class variable type_inst.start is: 1
Calling type_inst.a_method() returns: This is an instance of <class '__main__.a_type'>
```

The below print statement also gives the same result

print('The type of a_type() is: ', type(a_type()))

print('calling a_type().a_method() returns:', a_type().a_method())

### Basic class defination whic is same as above type defination
```python
class basic():
    start = 1

    def a_method(self):
        return 'This is an instance of ' + str(self.__class__)

basic_inst = basic()
print('The type of a_type is: ', type(basic))
print('The type of basic_inst is: ', type(basic_inst))
print('Class variable basic_inst.start is:', basic_inst.start)
print('Calling basic_inst.a_method() returns:', basic_inst.a_method())
```
result:
```pyton
The type of a_type is:  <class 'type'>
The type of basic_inst is:  <class '__main__.basic'>
Class variable basic_inst.start is: 1
Calling basic_inst.a_method() returns: This is an instance of <class '__main__.basic'>
```

# Steps to import python module into python shell 
### let say I wnat to import c:\user\sakti\test1.py into python shell

### Check python path environment variable 
``` python
import os
os.environ['PYTHONPATH']
```
### To check current system variable 
```python
import sys
sys.path
```
### To include 
```python
sys.path.append('c:\\user\\sakti\\')
import test1
```
### or
```python
os.chdir('c:\\user\\sakti\\')
import test1
```
### however the above chdir wont reflect the change made in the module later even import the moduel post the change aswell.
### In that case you have to reload the library to reflect the change in the module as like below.
```python
import importlib
importlib.reload(test1)
```
# addition of object
```python
class Vector(object):
    ''' A class for 2D vector which implements vector addition '''
    def __init__(self,x,y):
        ''' Initialize the vector object '''
        self.x = x
        self.y = y
        
    def __add__(self, other):
        ''' Implement the mecthod for "+" operatior '''
        x = self.x + other.x
        y = self.y + other.y
        return Vector(x,y)

    def __repr__(self):
        ''' Provide the usefull representation of the Vector object '''
        return 'Vctor(' + str(self.x) + ',' + str(self.y) + ')'

>>> alpha = Vector(3,4)
>>> beta =Vector(5,6)
>>> gama = alpha + beta
>>> gama
Vctor(8,10)
>>> print(gama)
Vctor(8,10)
```
# Different argument pass to function

## no argument to function
```python
def fun1():
    print('zero argument passed')
fun1()
```
## two argument
```python
def fun2(a,b):
    return a + b
print(fun2(2,3))
```
## unlimited number of arguments
```python
def fun3(*args):
    tot = 0
    for arg in args:
        tot +=arg
    return tot
print(fun3(3,4,5,6,7,8))
```
## passing a list / tuple
```python
var1=(1,2,3,4,5)
print(fun3(*var1))
```
## passing arguments using named parameters and default arguments
```python
def fun4(p1,p2=3,p3=4):
    return p1,p2,p3
print(fun4('required one argunent')
print(fun4('1','2','3'))
print(fun4(p2=4,p1='9',p3='1'))
```
## passing dictionary
```python
def fun5(**kwargs):
    for key in kwargs:
        print(key,'->',kwargs[key])
    return tuple(kwargs.values())
abc = {}
print(fun5(**abc))
pqr={'a':'1','b':'2','c':'3'}
print(fun5(**pqr))
```
output:

```python
>>> abc = {}
>>> print(fun5(**abc))
()
>>> pqr={'a':'1','b':'2','c':'3'}
>>> print(fun5(**pqr))
a -> 1
b -> 2
c -> 3
('1', '2', '3')
```

# In the script to call a function up on direct execution of the script and not to call it upon import, then use the \_\_name\_\_ == '\_\_main\_\_' condition
```python
if __name__ == '__main__':
    print(fun1())
```
