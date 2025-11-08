```python
secret_word = "Hello"  
guess = ""  
guesscount = 0  
guesslimit = 3  
in_guesses = True  
while guess != secret_word and in_guesses:  
    guess = input("enter your guess: ")  
    guesscount = guesscount + 1  
    if guesscount >= guesslimit:  
        in_guesses = False  
if guess == secret_word:  
    print("Congrats you won the game!")  
else:  
    print("Sorry, you lost the game!")```

**==BULDING A TRANSLATOR==**
```python
def translate(phrase):  
    translation = ""  
    for word in phrase:  
         if word.lower() in "aeiou":  
             if word.islower():  
                  translation = translation + "g"  
             else:  
                 translation = translation + "G"  
         else:  
            translation = translation + word  
    return translation  
print(translate(input("enter the word:")))

@this Is a hitech translator which can convert an vowel into g.