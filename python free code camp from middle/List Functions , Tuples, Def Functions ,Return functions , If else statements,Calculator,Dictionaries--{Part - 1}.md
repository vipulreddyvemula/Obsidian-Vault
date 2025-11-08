```python
##LIST FUNCTIONS
#1st function
friends = ["Nikhil","Vipul","Saketh","Vipul","Brijesh"]  
numbers = [1,2,3,4,5]  
friends.extend(numbers)  
print(friends)
result = ['Nikhil', 'Vipul', 'Saketh', 'Vipul', 'Brijesh', 1, 2, 3, 4, 5]
@to add two function.


#2nd function
freinds.append("People")
print(friends)
result = ['Nikhil', 'Vipul', 'Saketh', 'Vipul', 'Brijesh', 'People']
@to add an item to list.

#3rd function.
freinds.insert(1,"People")
print(friends)
result = ['Nikhil', 'People', 'Vipul', 'Saketh', 'Vipul', 'Brijesh']
@to insert an element into list by using the number of place.

#4th function
freinds.remove("People")
print(friends)
result = ['Vipul', 'Saketh', 'Vipul', 'Brijesh']
@to remove an item of list.

#5th function
friends.clear()
print(friends)
result = []
@to clear all items.

#6th funtcion
freinds.pop()
print(friends)
result = ['Nikhil', 'Vipul', 'Saketh', 'Vipul']
@removes last element oR pops out last elemnt.

#7th function
print(friends.index("Vipul"))
result = 1
@to find element number.

#8th function
print(friends.count("Vipul")
result = 2
@to count how many time the element repeats.

#9th function
friends.sort()  
print(friends)
result = ['Brijesh', 'Nikhil', 'Saketh', 'Vipul', 'Vipul']
@to sort iN alphabetical order.

#10th function
friends.reverse()  
print(friends)
result = ['Brijesh', 'Vipul', 'Saketh', 'Vipul', 'Nikhil']
@gives the elements wIth reverse aS of entered.

#11th function
friends2 = friends.copy()  
print(friends2)
result = ['Nikhil', 'Vipul', 'Saketh', 'Vipul', 'Brijesh']
@to copy one list to other.
_____________________________________________________________________________

###TUPLES
coordinates = (6,9), (2,4)  
coordinates[1] = (3,5)  
print(coordinates)
result = ERROR
@tupples are called immutable aNd once entered cant be changed like iN above example we tried to change but we couldnt to counter this we can transform a tuple into list like this .example1:
coordinates = [(6,9), (2,4)]  
coordinates[1] = (3,5)  
print(coordinates)
result = [(6, 9), (3, 5)]
@example2:
coordinates = [(6,9), (2,4)]  
coordinates[1] = (3,5)  
print(coordinates[1])
result = (3,5)

_____________________________________________________________________________
##HEADING
DEF FUNCTIONS:-
example1:-
def hello():  
    print("Hello World")  
hello()

result = Hello World
@take aS to define print.
example2:-
def airtel(user , age):  
    print("Hi " + user + " ,Your age is " + str(age))  
airtel("Vipul" ,17)  
airtel("kanna" ,18)

result = Hi Vipul ,Your age is 17
         Hi kanna ,Your age is 18

_____________________________________________________________________________

###RETURN FUNCTIONS
RETURN FUNCTIONS:-

def cub(num):  
    return num*num*num  
print(cub(5))

result = 125 

@In Python, the `return` statement is used inside a function to give back a result or value when the function is done.

example2:-
def square(num):
    return num * num

result = square(4)
print(result)  # Output: 16

bestexample3:- -============
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # Output: 8

-----------------------------------------------------------------------------
###==****if and else statements****==
if and else statements:-

laptop = False  
phone = True  
  
if laptop and phone:  
    print("Laptop and Phone")  
elif not(laptop) and phone:  
    print("Phone")  
elif laptop and not(phone):  
    print("Laptop")  
else:  
    print("No laptop and phone")

Result = Phone

 |Operator|        Meaning         |Example |Result|
 |--------|------------------------|--------|------|
1|  `==`  |    Equal to            |`5 == 5`|`True`|
2|  `!=`  |    Not equal to        |`5 != 3`|`True`|
3|   `>`  |    Greater than        |`5 > 3` |`True`|
4|   `<`  |    Less than           |`3 < 5` |`True`|
5|  `>=`  |Greater than or equal to|`5 >= 5`|`True`|
6|  `<=`  |Less than or equal to   |`3 <= 5`|`True`|

example2:-
def max(num1, num2 , num3):  
    if num1 > num2 and num1 > num3:  
        print(num1)  
    elif num2 > num1 and num2 > num3:  
        print(num2)  
    elif num3 > num1 and num3 > num2:  
        print(num3)  
max(30,10,2)

result = 30

-----------------------------------------------------------------------------
###**====BULDING CALCULATOR====**
==**BULDING CALCULATOR**==
num1 = float(input("Enter the first number: "))  
op = input("Enter the operation: ")  
num2 = float(input("Enter the second number: "))  
if op == "+":  
    print(num1 + num2)  
elif op == "-":  
    print(num1 - num2)  
elif op == "*":  
    print(num1 * num2)  
elif op == "/":  
    print(num1 / num2)  
else :  
    print("Invalid operation")

@THAT'S IT A CALCULATOR

_____________________________________________________________________________
###
****==*DICTIONARIES*==****

monconversions = {  
    "Jan" : "January",  
    "Feb" : "February",  
    "Mar" : "March",  
}  
print(monconversions["Jan"])    or print(monconversions.get("Jan"))
result = January                   result= January

@for the keys not in dictionary
print(monconversions.get("Jun")) or print(monconversions.get("Jun","June"))
result = None                       result= June

@things inside dictionaries are called keys
-----------------------------------------------------------------------------
###
****==*WHILE LOOPS*==****
w = 1  
while w <= 4:  
    print(w)  
    w += 1       (OR)  w = w+1
print("Hello World)
    result = 1
             2
             3
             4
             