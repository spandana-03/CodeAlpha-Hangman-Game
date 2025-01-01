 #CodeAlpha-Hangman-Game
import random
def hangman():
    # Predefined list of words
    words = ["python", "hangman", "programming", "developer", "keyboard"]
    word_to_guess = random.choice(words).lower()
    guessed_word = ["_"] * len(word_to_guess)
    attempts = 6
    guessed_letters = set()

    print("Welcome to Hangman!")
    print("You have 6 attempts to guess the word.")
    print(" ".join(guessed_word))
    
    while attempts > 0 and "_" in guessed_word:
        guess = input("\nGuess a letter: ").lower()

        if len(guess) != 1 or not guess.isalpha():
            print("Invalid input! Please guess a single letter.")
            continue

        if guess in guessed_letters:
            print(f"You've already guessed '{guess}'. Try another letter.")
            continue

        guessed_letters.add(guess)

        if guess in word_to_guess:
            print(f"Good job! '{guess}' is in the word.")
            for i, letter in enumerate(word_to_guess):
                if letter == guess:
                    guessed_word[i] = guess
        else:
            attempts -= 1
            print(f"Wrong guess! '{guess}' is not in the word. Attempts left: {attempts}")

        print(" ".join(guessed_word))

    if "_" not in guessed_word:
        print("\nCongratulations! You guessed the word:", word_to_guess)
    else:
        print("\nYou ran out of attempts! The word was:", word_to_guess)

if _name_ == "_main_":
    hangman()
