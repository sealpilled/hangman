### What you'll learn
- Setting up a Python project.
- Working with lists, strings, and basic game logic.
- Implementing loops, conditionals, and user input handling.
- Managing game states using a graphical representation of the hangman.

### Prerequisites
- Basic knowledge of Python (functions, loops, conditionals).
- Python installed on your computer.
- Basic understanding of Git.

## Step 1: Setting Up Your Environment

### 1.1. Clone the Hangman Template

First, you'll download a template containing the hangman states. This template will provide the initial setup needed to get started quickly.

#### Steps:

1. Open your terminal or command prompt.
2. Navigate to the directory where you want to set up your project.
3. Clone the template repository by running the following command:

    ```bash
    git clone https://github.com/your-username/hangman-template.git
    ```

4. Change into the project directory:

    ```bash
    cd hangman-template
    ```

### 1.2. Inspect the Template Files

After cloning the template, inspect the initial setup provided.

#### Check the Template:
- Open the `hangman.py` file in your preferred code editor.
- You should see the hangman stages defined in the file.

#### Example from the Template:
```python
HANGMAN = (
"""
-----
|   |
|
|
|
|
|
|
|
--------
""",
# Additional stages will be added here...
)
```

### Explanation:
- The `HANGMAN` variable contains different stages of the hangman drawing.
- This template serves as the starting point to develop the full Hangman game.

## Step 2: Printing the Welcome Message

### 2.1. Print the Welcome Message

Let's start by adding a welcome message to the player when they start the game.

#### Code:
```python
def main():
    welcome = ['Welcome to Hangman! A word will be chosen at random and',
               'you must try to guess the word correctly letter by letter',
               'before you run out of attempts. Good luck!']

    for line in welcome:
        print(line)
```

### Explanation:
- A list `welcome` contains strings for the welcome message.
- The loop prints each line of the welcome message to the player.

## Step 3: Starting the Main Game Loop

### 3.1. Loop for Playing Again

Allow the player to replay the game without restarting the program.

#### Code:
```python
    play_again = True

    while play_again:
        # Game logic will go here
```

### Explanation:
- A `play_again` variable determines whether the game should start a new round.
- The `while` loop continues as long as the player wants to play.

## Step 4: Choosing a Word and Setting Up the Game

### 4.1. Choosing a Random Word

Set up a list of possible words and select one randomly for the game.

#### Code:
```python
        words = ["hangman", "chairs", "backpack", "bodywash", "clothing",
                 "computer", "python", "program", "glasses", "sweatshirt",
                 "sweatpants", "mattress", "friends", "clocks", "biology",
                 "algebra", "suitcase", "knives", "ninjas", "shampoo"]

        chosen_word = random.choice(words).lower()
        player_guess = None
        guessed_letters = []
        word_guessed = ["-"] * len(chosen_word)
```

### Explanation:
- A list `words` contains potential words for the game.
- A random word is chosen using `random.choice()`.
- Initialize variables for player's input, guessed letters, and a list of dashes representing unguessed letters.

## Step 5: Displaying the Hangman Stages

### 5.1. Using the Hangman Stages

Use the hangman stages defined in the template to show the player's remaining attempts visually.

#### Code:
```python
        print(HANGMAN[0])
        attempts = len(HANGMAN) - 1
```

### Explanation:
- Display the initial hangman stage.
- Set the number of attempts based on the number of stages available in `HANGMAN`.

## Step 6: Running the Game Loop

### 6.1. Implementing the Guessing Loop

Implement the main game loop where the player guesses letters.

#### Code:
```python
        while attempts != 0 and "-" in word_guessed:
            print(f"\nYou have {attempts} attempts remaining")
            print("".join(word_guessed))

            player_guess = input("\nPlease select a letter between A-Z\n> ").lower()

            if not player_guess.isalpha() or len(player_guess) > 1 or player_guess in guessed_letters:
                print("Invalid guess. Please try again.")
                continue

            guessed_letters.append(player_guess)

            if player_guess in chosen_word:
                for i in range(len(chosen_word)):
                    if player_guess == chosen_word[i]:
                        word_guessed[i] = player_guess
            else:
                attempts -= 1
                print(HANGMAN[len(HANGMAN) - attempts - 1])
```

### Explanation:
- The loop continues while attempts are left and the word is not fully guessed.
- Player input is validated and compared against the chosen word.
- Correct guesses reveal letters, while incorrect guesses reduce attempts.

## Step 7: Ending the Game

### 7.1. Determine Win or Loss

After the loop ends, determine whether the player has won or lost.

#### Code:
```python
        if "-" not in word_guessed:
            print(f"\nCongratulations! {chosen_word} was the word.")
        else:
            print(f"\nUnlucky! The word was {chosen_word}.")
```

### Explanation:
- Check if there are any dashes left in `word_guessed` to determine if the player guessed the word.
- Display a win or loss message accordingly.

### 7.2. Prompt to Play Again

Ask the player if they want to play again.

#### Code:
```python
        print("\nWould you like to play again?")
        response = input("> ").lower()
        if response not in ("yes", "y"):
            play_again = False
```

### Explanation:
- Prompt the user for their input on whether to play another round.
- Update the `play_again` variable based on their response.

## Congratulations!

You've successfully built a Hangman game in Python! Feel free to modify the code, add more words, or enhance the game with additional features. Keep practicing, and enjoy coding!
