import random
import os
#keeps track of score

# Game settings and score count
MIN_NUMBER = 1
MAX_NUMBER = 75
MAX_ATTEMPTS = 5
SCORE_FILE = "best.score.txt"

# Loads the previous score
def load_best_score():
    if not os.path.exists(SCORE_FILE):
        return 6  # No score yet (defaults to higher than max attempts)
    try:
        with open(SCORE_FILE, "r") as file:
            content = file.read().strip()
            return int(content) if content else 6
    except:
        return 6

# Saves the score
def save_best_score(score):
    with open(SCORE_FILE, "w") as file:
        file.write(str(score))

# Starts the game
def play_game():
    best_score = load_best_score()
    if best_score <= MAX_ATTEMPTS:
        print(f"Current Best Score: {best_score} attempt(s)")
    else:
        print("Current Best Score: No score yet!")
        
    computer_number = random.randint(MIN_NUMBER, MAX_NUMBER)
    
    print("\n================================")
    print("      Welcome to Numble!        ")
    print("================================")
    print(f"I am thinking of a number between {MIN_NUMBER} and {MAX_NUMBER}!")
    print("Can you try to guess it?")
    
    # Attempts loop
    for attempt in range(1, MAX_ATTEMPTS + 1):
        try:
            guess = int(input(f"\nAttempt {attempt}/5 - Guess a number: "))
        except ValueError:
            print("Please enter a valid number!")
            continue

        if guess < MIN_NUMBER or guess > MAX_NUMBER:
            print(f"Please enter a number between {MIN_NUMBER} and {MAX_NUMBER}!")
            continue

        if guess == computer_number:
            print("\nWow! You guessed it correctly.")
            print(f"The number was: {computer_number}")
            print(f"Your score: {attempt} attempt(s)")
            
            # New high score (lower attempts is better)
            if attempt < best_score:
                save_best_score(attempt)
                print("Congratulations! You broke the high score.")
            break
        elif guess < computer_number:
            print("Too low! Try a higher number.")
        else:
            print("Too high! Try a lower number.")
    else:
        # Executes if the loop finishes without a 'break' (all attempts used)
        print("\nGame Over! You used all 5 attempts.")
        print(f"The correct number was: {computer_number}")
        print(f"Best Score: {best_score if best_score <= MAX_ATTEMPTS else 'No score yet!'}")

# Allow to play again
while True:
    play_game()
    again = input("\nWould you like to play again? (yes/no): ").strip().lower()
    if again not in ["yes", "y"]:
        print("\nThanks for playing!")
        break




  
