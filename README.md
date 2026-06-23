import random

# List of predefined words
words = ["python", "computer", "hangman", "program", "coding","developer","software","database","website","algorithm","function","variable","loop","condition","array"]

# Choose a random word 
word = random.choice(words)

# Create hidden version of the word
guessed_word = ["_"] * len(word)

# Track guessed letters and remaining attempts
guessed_letters = []
attempts = 6

print("Welcome to Hangman!")

while attempts > 0 and "_" in guessed_word:
    print("\nWord:", " ".join(guessed_word))
    print("Incorrect guesses left:", attempts)
    print("Guessed letters:", ", ".join(guessed_letters))

    guess = input("Guess a letter: ").lower()

    # Check if input is valid
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single letter.")
        continue

    # Check if letter was already guessed
    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    # Check if guess is in the word
    if guess in word:
        print("Correct!")

        # Reveal matching letters
        for i in range(len(word)):
            if word[i] == guess:
                guessed_word[i] = guess
    else:
        print("Wrong guess!")
        attempts -= 1

# End of game
if "_" not in guessed_word:
    print("\nCongratulations! You guessed the word:", word)
else:
    print("\nGame Over! The word was:", word)
