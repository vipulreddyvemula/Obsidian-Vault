```python
                       {{{{###==FOR LOOPS==###}}}}
@in strings
for program in "telecom":  
    print(program)      #result= t,e,l,e,c,o,m.

@in numbers
for program in range(3):  
    print(program)      #RESULT = 0 ,1 ,2
@OR
for program in range(1,5):  
    print(program)      #RESULT = 1,2,3,4.
    
@in lists
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)        #RESULT = apple
                                  banana
                                  cherry

# @we can modify still and use it,we can also use if and else statements.
-----------------------------------------------------------------------------
####**==*Exponent Functions*==**
@generall exponet function is
print(a**b)
result = a^b          if (a,b) is (2,3) result = 8

##using for loops
def listout(down,up):  
    result = 1  
    for x in range(up):  
        result = result * down  
    return result  
print(listout(5,4))               #finalresult = down^up
_____________________________________________________________________________

                        **====2D LISTS====**
matrix = [  
    [1,2,3,],  
    [4,5,6,],  
    [7,8,9]  
]  
print(matrix[0][0])  # Output: 1
print(matrix[1][1])  # Output: 5
print(matrix[2][2])  # Output: 9

matrix = [  
    [1,2,3,],  
    [4,5,6,],  
    [7,8,9]  
]  
 for row in matrix:
     print(row)   #result = [1, 2, 3]
                            [4, 5, 6]
                            [7, 8, 9]

&&==**nested lists i.e a double for loop**==&&

for row in matrix:
    for col in row:
       print(col)      #result = 1,2,3,4,5,6,7,8,9

-----------------------------------------------------------------------------
COMMENTS
comments can be written inside our python code which python doesnt not execute or render them , we can write a comment by just using a hasttag infront of a comment or a line of code which we want to turn into a comment.

_____________________________________________________________________________```
==**TRY/EXCEPT BLOCKS**==
```python
try:  
    range = int(input("Enter a number: "))  
    print(range)  
except:  
    print("invalid")   #on entering a letter it prints invalid

@we can enter multiple excepts blocks by  using the error name.example1
try:  
    value = 10 / 0  
    range = int(input("Enter a number: "))  
    print(range)  
except ZeroDivisionError:  
    print("Entered zero")  
except ValueError:  
    print("Entered letters")

@storing error aS variable.example2
try:  
    value = 10 / 0  
    range = int(input("Enter a number: "))  
    print(range)  
except ZeroDivisionError as err:  
        print(err)  
except ValueError:  
    print("Entered letters")               #result = division by zero
p


