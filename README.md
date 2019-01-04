# Python class and type
### Python classes are all types.

Type is nothing but called template of an object.

The builtin calsses have their own types.

User-defined classes can inharite their types
fron the builtin classes or the generic type.

The type function can display the type of an object and can also used to define a new type.

Where the class statement is typically used to define a new type.

Typically the type function is not used to create classes,
instead we use class statement to do so.


### Type function used to display the type
```python
print('The type of 1 is:', type(1))
print('The type of [] is:', type([]))
```

### Type function used to define a type
below is the basic defination of type
```python
a_class = type('a_class',(),{}) 
print('The Type of a_type is: ', type(a_class))
an_inst = a_class()
print('The Type of an_inst is: ', type(an_inst))
```

### Below is the type defination with attributes
```python
a_type=type('a_type',(),{'start':1,'a_method':
             lambda self: 'This is an instance of ' +
             str(self.__class__)})
type_inst = a_type()
print('The Type of a_type is: ', type(a_type))
print('The Type of type_inst is: ', type(type_inst))
print('Class variable type_inst.start is:', type_inst.start)
print('calling type_inst.a_method() returns:', type_inst.a_method())
```

print('The Type of a_type() is: ', type(a_type()))
print('calling a_type().a_method() returns:', a_type().a_method())

### Basic class defination whic is same as above type defination
```python
class basic():
    start = 1

    def a_method(self):
        return 'This is an instance of ' + str(self.__class__)

basic_inst = basic()
print('The Type of a_type is: ', type(basic))
print('The Type of type_inst is: ', type(basic_inst))
print('Class variable type_inst.start is:', basic_inst.start)
print('calling type_inst.a_method() returns:', basic_inst.a_method())
```


    
