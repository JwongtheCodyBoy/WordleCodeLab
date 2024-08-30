author: Jonathan Wong
summary:
id: WordleCodeLab
tags: Python
categories: USF Game Development Workshop
environments: Web
status: Published
feedback link: https://github.com/SolaceDev/solace-dev-codelabs/blob/master/markdown/WordleCodeLab

# Wordle Workshop Game Devlopment Club

## What you'll learn: Overview

Duration: 0:05:00

Make Wordle in Python terminal in about 48 lines of code 

### Table of Content
1. Setup Enviorment 
1. Setting the template and Intro function
1. Input and word logic cases
1. Word guess logic
1. Use a text file instead of a word list

### Add an Image or a GIF

![Soly Image Caption](img/soly.gif)

## Setup Enviorment 

Duration: 0:07:00

Only need two things:
* VS code
* Python

Get Visual Studio Code because why use any other IDEs [Download VS Code](https://code.visualstudio.com/download)
<br>

Get Python from Python website,
[Click Here!](https://www.python.org/downloads/)


## Setting the template and Intro function

Duration: 0:04:00

### What is Wordle and what does it need?
Wordle is a word guessing game, that the user guess a random word and get clues based on past guess

So some things we will need, randomness, and a word bank and game logic.

```
import random

words = ['gamed', 'usfgdc', 'tired', 'cofee', 'ineed']

def main():

main()
```

### Probably a good idea to include some Instructions to the game at the top, so lets add a function
```
def Intro():
    print("This is Wordle")
    print("\t✅ - letter is the word and is in correct spot")
    print("\t🟨 - letter is the word and is not in the right spot")
    print("\t _ - letter is not in the word")
    print()
```

Call the function in your main 
```
import random

words = ['gamed', 'usfgdc', 'tired', 'cofee', 'ineed']

def Intro():
    ...

def main():
    Intro()
    
main()
```

### Picking a random word in the word bank
```
def main():
    Intro()
    hiddenWord = words[random.randint(0, len(words)-1)]
```

Also wordle has a limited number of trys, so lets add that too.
```
hiddenWord = words[random.randint(0, len(words)-1)]
attempts = 5    # NEW CODE HERE
```

## Input and word logic cases

Duration 0:07:00

### Design and Logic
What we want:
* While user still has an attempt left, allow them to guess
* Take the user's input/guess
* If User guess the hidden word then end game, Otherwise do some wordle game logic to give a glue
* Remove an attempt per guess and tell the player

```
def main():
    Intro()
    hiddenWord = words[random.randint(0, len(words)-1)]
    attempts = 5

    # NEW CODE HERE
    while (attempts > 0):
        guess = input("Enter Guess (5 Letter Word): ").lower()

        if (guess == hiddenWord):
            print("Good Guess!!!")
            break
        else:
            # Do wordle clue logic
        
        attempts -= 1
        print(f"{attempts} are left.\n")
```

## Word guess logic

Duration: 0:07:00

### Design and Logic
* Create an output that tells us something about the hidden word 
* Check for every letter in the guess If it is in the same spot of the hidden word, give it a checkmark
* else if the letter is in the word, mark it as yellow
* otherwise leave it blank

### Doing it in code
```
if (guess == hiddenWord):
    print("Good Guess!!!")
    break
else:
    # NEW CODE HERE
    output = ""
    for hiddenLetter, guessLetter in zip(hiddenWord, guess):
        if (hiddenLetter == guessLetter.lower()):
            output += " ✅ "
```

Since if statements will skip else-if and else statements when true, we can just stack these statements logically for easy implementation
```
else:
    output = ""
    for hiddenLetter, guessLetter in zip(hiddenWord, guess):
        if (hiddenLetter == guessLetter.lower()):
            output += " ✅ "

        # NEW CODE HERE
        elif (guessLetter in hiddenWord):
            output += " 🟨 "
        else:
            output += " _ "

    print(output)       #outside of the loop
``` 

## Use a text file instead of a word list

Duration: 0:08:00

### Lets reveal the secret word if user run out of attempts

```
            attempts -= 1
            print(f"{attempts} are left.\n")

# NEW CODE HERE
            if (attempts == 0): 
                print(f"All attempts were used, the word was {hiddenWord.upper()}.")
# NEW CODE END

main()
```

### Now Your wordle is already functional logically, HOORAY
However, you may notice that you can enter non-real words and it still runs unlike wordle

Additionally, you also may realize that if we want more words, we will have to expand our list which makes it ugly and wonder why do that manually

### Design and Logic
* Make it so that we can not guess random letters, and actually have to guess words
* Not take User's attempt or run logic not in our word bank
* Make it so that our word bank can be larger without bad code

### Coding our Design

```
while (attempts > 0):
    guess = input("Enter Guess (5 Letter Word): ").lower()

    # NEW CODE HERE
    if (guess not in words):            # because we are arrogant if we dont know it, it doesn't exist
        print("Word not in word list, Try another word\n")
        continue
    # NEW CODE END

    if (guess == hiddenWord):
            print("Good Guess!!!")
```

### Opening an external file in python
```
import random

# NEW CODE HERE
# wordslist.txt was taken from here https://gist.github.com/dracos/dd0668f281e685bad51479e5acaadb93
with open('wordslist.txt', 'r') as wordsFile:
    words = wordsFile.read().split('\n')

# words = ['gamed', 'usfgdc', 'tired', 'cofee', 'ineed']        Remove this if you want
```

## Wordle IS done

Duration: 0:01:00

✅ < Fill IN TAKEAWAY 1>   
✅ < Fill IN TAKEAWAY 2>   
✅ < Fill IN TAKEAWAY 3>   

![Soly Image Caption](img/soly.gif)

Thanks for participating in this codelab! Let us know what you thought in the [Solace Community Forum](https://solace.community/)! If you found any issues along the way we'd appreciate it if you'd raise them by clicking the Report a mistake button at the bottom left of this codelab.
