# hangman-python
Basic Hangman game
# 🪓 Hangman — Python Word Guessing Game

This is a simple Hangman game written in Python. The player guesses letters to uncover a hidden word. Miss too many and... well, you know what happens. 💀

## 🎮 How to Play

- You get 10 chances to guess the word
- Each wrong guess builds the hangman figure
- Game ends when you guess the word or run out of attempts

## 💻 Run Locally
import random

# Hangman stages (index 0 = full hangman, index 10 = no hangman)
hangman_stages = [
    '''
     +---+
     |   |
     O   |
    /|\\  |
    / \\  |
         |
    =========
    ''',
    '''
     +---+
     |   |
     O   |
    /|\\  |
    /    |
         |
    =========
    ''',
    '''
     +---+
     |   |
     O   |
    /|\\  |
         |
         |
    =========
    ''',
    '''
     +---+
     |   |
     O   |
    /|   |
         |
         |
    =========
    ''',
    '''
     +---+
     |   |
     O   |
     |   |
         |
         |
    =========
    ''',
    '''
     +---+
     |   |
     O   |
         |
         |
         |
    =========
    ''',
    '''
     +---+
     |   |
         |
         |
         |
         |
    =========
    ''',
    '''
     +---+
         |
         |
         |
         |
         |
    =========
    ''',
    '''
         
         
         
         
         
         
    =========
    ''',
    '''
         
         
         
         
         
         
         
    ''',
    '''
    
    
    
    
    
    '''
]

# Load dictionary (or use custom .txt file on Windows)
with open('/usr/share/dict/words') as f:
    word_bank = [w.strip().lower() for w in f if w.strip().isalpha() and 4 <= len(w.strip()) <= 8]

word = random.choice(word_bank)
guessedWord = ['_'] * len(word)
attempts = 10

# Game Loop
while attempts > 0:
    print(hangman_stages[10 - attempts])  # Show the correct hangman stage
    print('Current word: ' + ' '.join(guessedWord))
    guess = input('Guess a letter: ').lower()
    
    if guess in word:
        for i in range(len(word)):
            if word[i] == guess:
                guessedWord[i] = guess
        print('Great guess!')
    else:
        attempts -= 1
        print('Wrong guess! Attempts left: ' + str(attempts))
    
    if '_' not in guessedWord:
        print('\nCongratulations!! You guessed the word: ' + word)
        break

if attempts == 0 and '_' in guessedWord:
    print(hangman_stages[0])  # Final stage
    print('\nYou\'ve been hanged! The word was: ' + word)

```bash
git clone https://github.com/Misterfox089/hangman-python.git
cd hangman-python
python hangman.py
