# All You Need Know About Object Oriented Programming in Python

## Table of Contents
[Introduction](#intro)
[Object Oriented Programming Keywords](#OOP)
[Creating a template for an object](#temp)
[Creating An Instance](#inst)
[Creating getters for an object](#get)
[Creating set methods](#set)
[Inheritance](#inherit)
[Polymorphism](#poly)
[Encapsulation](#encap)
[Summary](#summary)

Object-oriented programming (OOP)<a name="intro"></a> is another programming paradigm that was derived from procedural programming. The first language to include object-oriented principles was called [Simula](https://en.wikipedia.org/wiki/Simula), released in 1967. Now a number of modern languages use or allow the use of OOP.

In object-oriented programming<a name="OPP"></a>, objects are used to model things in code. 

An object is a collection of data. Each object has the same basic attributes but the values may be different. 

Its associated actions is called methods.

In procedural programming, data is stored in the main program and passed to subroutines but in OOP the data and subroutines are stored together in objects which are created from classes.

The OOP paradigm is focused on objects which represent parts of a computer program. You can create objects to represent real physical things, like a human being. They can also be used for small parts of a larger program, like a widget in a user-interface.

### For Example:

![Car](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k8otzm8qane4wbmxkpvr.jpg)Object - Car 
Attributes - Make, model, colour 
Methods - Accelerate, slow down, change gear 

In this example, we could create lots of instances of cars of varying makes and models, all with different colours, but they are all the same type of object, sharing the same attributes.

![Instances of Cars](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9heyjm9sn8tco1ixx7ti.jpg)

To create objects you must first define a class. 

A class is like a blueprint, it contains the plans for the data and behaviours an object should possess. You can create many objects from a single class. Just like you can make many houses from the same blueprint.

![House Blueprint](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3zhd8m23b5xwhicebxqu.jpg)

A class needs a constructor. 

A constructor is a special type of method that initialises (constructs) an object of that type and defines what attributes the object has.
```python
joe = User("Joe Dalton", "joeboss@example.com")
```

This method is called to create a new instance of a class, a new object.

### Creating A Template for An Object <a name="temp"></a>

Start by creating an identifier for your class with the object you want to create, For example we are going to create an object for a bank account. 
```python
class Bank_account()
```
Next, we write the constructor, a special method to instruct Python how to create on object of this class.
```python
class Bank_account:
    def __init__(self, account_name, account_number, balance):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = balance
```

*init* here stands for ‘initialise’. In this example we can see the **Bank_account** will have a, account_name, _account_number_, and _balance_. These are the attributes that the **Bank_account** will have.

**Note:** If we set the attribute values to _None_, they would start off with no value.

We always refer to attributes within the object in the format _self.name_of_attribute_ to tell Python that we are referring to a piece of data within the object. 

_self_ means “this object”. 

Save this file as bank_account.py

### Creating An Instance of Bank_account<a name="inst"></a>
Now we have a class file for our object, we can go ahead and create a new instance of a **Bank_account.**

In a new file (but in the same folder as your class file), we are going to import the **_Bank_account_** object from our custom class file **_bank_account_**.
```python
from bank_account import Bank_account
```
Next, we need to define the attributes of our bank account. 
```python
from bank_account import Bank_account

account_a = Bank_account("John Dalton", "123456789", 1000)
```
Here we have created a variable called account_a. The account's name, has been assigned the value “John Dalton”, the account number has been assigned the value “123456789”, and a balance of _1000_ has been included. 

**Save** your new file as accounts.py.

If you now execute your accounts.py file you will not see any output. However an instance of your Bank account has been created in memory with the attributes assigned in accounts.py.

### Creating getters for an object<a name="get"></a>
To make use of information in our objects, we need to write some methods that give us access to it. 

These are called getters. They are essentially functions that can be called to get information about our objects.

```python
class Bank_account:
    def __init__(self, account_name, account_number, balance):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = balance

    def get_account_name(self):
        return self.account_name
```
Go back and open up **bank_accounts.py**. A method has been added above to get the name of the bank account. Can you add this, as well as two more methods to get the _account_number_, and the _balance_?
```python
class Bank_account:
    def __init__(self, account_name, account_number, balance):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = balance

    def get_account_name(self):
        return self.account_name
    
    def get_account_number(self):
        return self.account_number

    def get_balance(self):
        return self.balance
```
The getter methods here allow us to test and get information about our object. 

What will be displayed on the screen when this is executed?

As they just return the value, nothing will actually be printed to the screen. They are useful if we want to concatenate the information together. 

We can however print the result of calling these get methods.
```python
from bank_account import Bank_account

account_a = Bank_account("John Dalton", "123456789", 1000)

print(account_a.get_account_name())
```
```
John Dalton
>>>
```
Go back and open up accounts.py. Using a print statement, test that your getter methods are working. One has been done for you above.

```python
from bank_account import Bank_account

account_a = Bank_account("John Dalton", "123456789", 1000)

print(account_a.get_account_name())
print(account_a.get_account_number())
print(account_a.get_balance())
```
```
John Dalton
123456789
1000
>>>
```
Whilst this is a useful way of seeing information about our objects, a method could be included within the class itself to describe the object.

**Problem:** Instead of three separate print statements in your accounts.py file, we will now use a different approach. Go back to bank_accounts.py and add an additional method called display_info() which will print out the object’s attribute details when called.

**Solution**

```python
class Bank_account:
    def __init__(self, account_name, account_number, balance):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = balance

    def get_account_name(self):
        return self.account_name
    
    def get_account_number(self):
        return self.account_number

    def get_balance(self):
        return self.balance

    def display_info(self):
        print("Account Details: %s, %s, balance is %s" %(self.account_name, self.account_number, self.balance))
```
Go back and open up accounts.py. Using a print statement, test that your method is working.
```python
from bank_account import Bank_account

account_a = Bank_account("John Dalton", "123456789", 1000)

print(account_a.display_info())
```
```
Account Details: John Dalton, 123456789 balance is 1000
>>>
```
### Creating set methods <a name="set"></a>
Previously we created get methods to retrieve information about our objects. What if we want to set/change information? 

For this we use set methods that allow us to change information within our objects. An example set method has been created below
```python
class Bank_account:
     ...
     ...
     ...
     ...
     ...
     def set_account_name(self, account_name):
          self.account_name = account_name
```
Modify your _bank_account file_ to include the _set_account_name()_ method, and check it works by calling it in your accounts file using your _display_info()_ method. 

Can you create additional methods in your accounts.py file to set the account_number and the balance?
```python
class Bank_account:
    def __init__(self, account_name, account_number, balance):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = balance

    def get_account_name(self):
        return self.account_name
    
    def get_account_number(self):
        return self.account_number

    def get_balance(self):
        return self.balance

    def set_account_name(self, account_name):
        self.account_name = account_name

    def set_account_number(self, account_number):
        self.account_number = account_number

    def set_balance(self, balance):
        self.balance = balance

    def display_info(self):
        print("Account Details: %s, %s, balance is %s" %(self.account_name, self.account_number, self.balance))
```
### Inheritance<a name="inherit"></a>
Inheritance is a mechanism for basing one class off of another. 

The new class is called a subclass. The original class is a superclass. 

The subclass inherits all the attributes and methods of the superclass.

When you create a new subclass it inherits all the attributes and methods of the superclass. 

You can add new attributes and methods as well, allowing you to add specific data or actions that are only applicable to the subclass.

Here's an example of inheritance in Python:
```python
class Animal:
    def __init__(self, name):
        self.name = name
        
    def make_sound(self):
        print("Some animal sound")
        
class Dog(Animal):
    def make_sound(self):
        print("Woof!")
        
dog = Dog("Max")
dog.make_sound() Woof!

```
```
Woof!
>>>
```
In this example, the class Dog is a subclass of the class Animal, and it inherits the attribute name and the method make_sound from the superclass. However, the method make_sound is redefined in the subclass to provide a different implementation. This is a simple example. Hence, another example is here below...
```python
class Bank_account:
    def __init__(self, account_name, account_number, balance):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = balance

    def get_account_name(self):
        return self.account_name
    
    def get_account_number(self):
        return self.account_number

    def get_balance(self):
        return self.balance

    def set_account_name(self, account_name):
        self.account_name = account_name

    def set_account_number(self, account_number):
        self.account_number = account_number

    def set_balance(self, balance):
        self.balance = balance
class Credit(Bank_account):
    def __init__(self, account_name, account_number, balance, loans, liability):
        super.__init__(self, account_name, account_number, balance):
        self.loans = loans 
        self.liability = liability
    
    def get_loans():
        return self.loan

    def set_loans(self, loans):
        self.loans = loans

    def get_liability():
        return self.liability

    def set_liabilities(self, liability):
        self.loans = loans
```
Now open the accounts.py file, add the objects and print it's attributes
```python
from bank_account import Bank_account, Credit

account_a = Credit("John Dalton", "123456789", 1000, 2400, "Car")

print(account_a.get_liability())
```
```
Car
>>>
```
### Polymorphism<a name="poly"></a>
Polymorphism is a key feature of Object-Oriented Programming (OOP) in Python that allows you to use objects of different classes with a common interface (i.e. method names).

In polymorphism, objects of different classes can respond to the same method call in a unique way, as determined by the class of the object. This allows you to write code that can work with objects of different classes interchangeably, as long as they have a common interface.

There are two main types of polymorphism in Python:

Duck Typing: Duck typing is a dynamic typing approach that allows an object to be used as long as it has the required methods, regardless of the class it belongs to.

Method Overloading: Method overloading is a static typing approach that allows multiple methods with the same name, but with different parameters, in the same class or in different classes.

Here's an example of polymorphism in Python
```python
def make_sound(animal):
    animal.make_sound()

class Dog:
    def make_sound(self):
        print("Woof!")
        
class Cat:
    def make_sound(self):
        print("Meow!")
        
dog = Dog()
cat = Cat()
make_sound(dog)
make_sound(cat) 
```
```
Woof!
Meow!
>>>
```
In this example, the function make_sound takes an object of any class that has a method named make_sound and calls that method. The classes Dog and Cat both have a method make_sound, so they can be used interchangeably with the make_sound function.

This is just a simple example of polymorphism in Python. The concept of polymorphism is essential for writing robust and flexible code, and can be used in a variety of ways in OOP.

### Encapsulation<a name="encap"></a>
Encapsulation is a key feature of Object-Oriented Programming (OOP) in Python that allows you to control access to an object's attributes and methods. It helps you to hide the implementation details of an object and provide a public interface for accessing and using the object.

Encapsulation in Python is achieved by using the private and protected access modifiers. By convention, private attributes and methods in Python are denoted with a double underscore __ prefix, and protected attributes and methods are denoted with a single underscore _ prefix.

Here's an example of encapsulation in Python:
```python
class Bank_account:
    def __init__(self, balance):
        self.__balance = balance
        
    def get_balance(self):
        return self.__balance
        
    def deposit(self, amount):
        self.__balance += amount
        
    def withdraw(self, amount):
        if self.__balance >= amount:
            self.__balance -= amount
            return True
        else:
            return False
            
account = Bank_account(100)
print(account.get_balance()) 
account.deposit(50)
print(account.get_balance()) 
print(account.withdraw(200)) 
print(account.get_balance()) 
```
```
100
150
False
150
>>>
```
In this example, the class BankAccount has a private attribute __balance that stores the account balance, and several public methods for accessing and modifying the balance. The get_balance method returns the balance, the deposit method adds an amount to the balance, and the withdraw method subtracts an amount from the balance.

Encapsulation allows you to encapsulate the implementation details of an object and provide a public interface for using the object, making your code more maintainable and less prone to errors.

### Summary<a name="summary"></a>
Object oriented programming is a way of creating programs using classes. 

Classes are collections of data (attributes) and behaviours(methods). When we want to use the classes we create objects that we can manipulate in our programs.

Classes and objects hold information and behaviours. 

Attributes are the data that an object holds, it’s variables. 

Methods are an object’s actions, the things it can do. They are functions defined inside a class.

The principles of OOP guide the way you create programs and software. 

Inheritance allows you to derive classes from one another. 

The original class is called a superclass.

The new class is called a subclass.


Hope you enjoy the article, Please drop your comments...

Thank you...











