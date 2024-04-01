# Hangman.py
#Hangman game

import random

def choose_word():
    wordlist = ["apple", "banana", "orange", "strawberry", "grape", "watermelon"]
    return random.choice(wordlist)
#creating word list

def display_word(word, guessed_letters):
    displayed_word = ""
    for letter in word:
        if letter in guessed_letters:
            displayed_word += letter + " "
        else:
            displayed_word += "_ "
    return displayed_word.strip()
#display or user input sequence

def hangman():
    while True:  # Loop for restarting the game
        word = choose_word()
        guessed_letters = []
        attempts = 6

        print("\nWelcome to Hangman!")
        print("Try to guess the word(Hint: fruits).")
#attempts, saved guesses
        
        while attempts > 0:
#while attempts are still above zero, create a loop
            print("\nWord:", display_word(word, guessed_letters))
            print("Attempts left:", attempts)
            
            guess = input("Guess a letter: ").lower()
#user input
            if len(guess) != 1 or not guess.isalpha():
                print("Please enter a single letter.")
                continue
#if guess is not equal to 1 letter or if it is not a letter
            if guess in guessed_letters:
                print("You already guessed that letter.")
                continue
#if guess has already been guessed
            guessed_letters.append(guess)
#add all guesses to guessedletters folder
            if guess not in word:
                print("Incorrect guess!")
                attempts -= 1
            else:
                print("Correct guess!")
#if guess is not in word, deduct 1 attempt
            if all(letter in guessed_letters for letter in word):
                print("\nCongratulations! You guessed the word:", word)
                break
#if all letters have been guessed in the sequence
#congrat and break the sequence
        if attempts == 0:
            print("\nYou ran out of attempts! The word was:", word)
#if attempts reach 0, game over
        play_again = input("Do you want to play again? (yes/no): ").lower()
        if play_again != "yes":
            break
#the game is already in a loop through while true statement
#if user says no, we break the loop
hangman()
