The Task is to Create Hangman in Python

# Basic Flowchart:

![](Pictures/Hangman%20Project%20-%20Basic%20Flowchart.png)

# To-do List:
## Step 1:

- [x]  Randomly choose a word from the word_list and assign it to a variable called chosen_word. Then print it.

- [x] Ask the user to guess a letter and assign their answer to a variable called guess. Make guess lowercase.

- [x] Check if the letter the user guessed (guess) is one of the letters in the chosen_word. Print "Right" if it
## Step 2:

- [x] To-do 1:
	- [x] Create an empty String called `placeholder`.
	- [x] For each letter in the chosen_word, add a `_` to `placeholder`.
	- [x] So if the `chosen_word` was "apple", `placeholder` should be `_ _ _ _ _` with 5 `"_"` representing each letter to guess.
	- [x] Print out `hint`.

**Remember:** you can use the range() function inside a loop to carry out an action for a particular number of times. 

- [x] To-do 2:
	- [x] Create an empty string called "display".
	- [x] Loop through each letter in the `chosen_word`
	- [x] If the letter at that position matches `guess` then reveal that letter in the `display` at that position.
	- [x] e.g. If the user guessed "p" and the chosen word was "apple", then `display` should be `_ p p _ _`.
	- [x] Print `display` and you should see the guessed letter in the correct position.
	- [x] But every letter that is not a match is represented with a `"_"`.

**Remember:** that the for loop will go through each letter in the chosen_word in order. You can use that fact to create a new string, appending the letter or an `"_"`.
## Step 3:

- [x] To-do 1:
	- [x] Use a while loop to let the user guess again. 
	- [x] The loop should only stop once the user has guessed all the letters in the chosen_word.
	- [x] At that point `display` has no more blanks (`"_"`). Then you can tell the user they've won.

**Hint:** You can use the in keyword to check if a String or List contains a particular item. e.g. Google: check if a letter is present in a string python 

- [x] To-do 2:
	- [x] Update the for loop so that previous guesses are added to the `display` String.
	- [x] At the moment, when the user makes a new guess, the previous guess gets replaced by a `"_"`. We need to fix that by updating the for loop.

**Hint:** Think about how you can store the matched letters and use an elif to check if a letter has been matched before.
## Step 4:

- [x] To-do 1:
	- [x] Create a variable called `lives` to keep track of the number of lives left.
	- [x] Set `lives` to equal `6`.

- [x] To-do 2:
	- [x] If `guess` is not a letter in the `chosen_word`, Then reduce `lives` by `1`. 
	- [x] If `lives` goes down to `0` then the game should end, and it should print "You lose."

**Hint:** The not in keywords will be your friend in this todo. You can check if something exists in the chosen_word completely separately from the rest of the code. 

- [x] To-do 3:
	- [x] print the ASCII art from the list `stages` that corresponds to the current number of `lives` the user has remaining.
#  The `in` Keyword:

To check if the string contains a letter I've decided to first convert it to a list so that I can modify elements of the string as this is something that is not possible for the string datatype in python. Then I've created the following function to check for an underscore in the list:

```python
def listContainsUnderscore(list):
    for l in list:
        if l == "_":
            return True
    return False
```

However, it's possible to use the `in` keyword to check if a string contains a specific character:

```python
display = "a__dr_"
if "_" not in display: # false

if "_" in display: # true
```
# The `from` Keyword:

It's possible to create a "namespace" for a module by using the `from` keyword.

Suppose we have a module named `hangman_words` and we would like to access a list from it called `word_list`.

Normally we would do the following:

```python
print(hangman_words.word_list)
```

but we can also use the `from` keyword and access it in this way:

```python
from hangman_words import word_list

print(word_list)
```

# My Solution

```python nums
import os
import platform
import random

import hangman_ascii
import words

clear = lambda: (
    os.system("cls") if platform.system() == "Windows" else os.system("clear")
)
clear()
print(hangman_ascii.HANGMAN_LOGO)

def listToString(list):
    string = ""
    for l in list:
        string += l
    return string


def listContainsUnderscores(list):
    if "_" in list:
        return True
    else:
        return False


def listContainsGuess(list, guess):
    if guess in list:
        return True
    else:
        return False


lives = 6

print(f"Lives remaining: {lives}")
print(hangman_ascii.HANGMAN_PICS[-lives - 1])

chosen_word = random.choice(words.WORD_LIST)

display = list("_" * len(chosen_word))
print(listToString(display))

while listContainsUnderscores(display) and lives != 0:
    guess = input("Guess a letter: \n")
    clear()

    for i in range(len(chosen_word)):
        if chosen_word[i] == guess:
            display[i] = guess
            print(f"You guessed correctly, {guess} is a letter in the word")

    if not listContainsGuess(display, guess):
        lives -= 1
        print(f"You guessed incorrectly, {guess} is not a letter in the word")

    print(f"Lives remaining: {lives}")
    print(hangman_ascii.HANGMAN_PICS[-lives - 1])
    print(listToString(display))
    if lives == 0:
        print("You lose")
    if not listContainsUnderscores(display):
        print("You win")
```