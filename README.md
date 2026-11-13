import random
import os
#keeps track of score
import datetime import datetime 
#keep record of each attempt

#score count

SCORE_FILE = "best.score.txt"

#dictionary that stores difficulty settings
Game_Modes = {
    "1": {
        "name": "Simple",
        "minimum": 1,
        "maximum": 50,
        "attempts": 8,
    },
    
    "2": {
        "name": "Normal",
        "minimun": 1,
        "maximum": 100,
        "attempts": 6,
    }
    
    "3": {
        "name": "Complex",
        "minimum": 1,
        "maximum": 500,
        "attempts": 4
    }
}

def display_title():
    print("\n================================")
    print("      Welcome to Numble!        ")
    print("================================")
    print("I am thinking of a number!")
    print("Can you try to guess it?")
    
def display_modes():
    print("\nPick your skill level")
    print("-" * 30)
    
    print("1. Simple Mode")
    print("   Number range 1-50")
    print("   Attempts: 8")
    
    print()
    print("2. Normal Mode")
    print("   Number range 1-50")
    print("   Attempts: 8")
    
    print ()
    
    print("3. Complex Mode")
    print("   Number range 1-50")
    print("   Attempts: 8")
    
    print ("-"* 30)
    
# Loads and stores the previous scores
def load_best_scores():
    best_scores = {
        "Simple": None,
        "Normal": None,
        "Complex": None
    }
    
    if  os.path.exists(SCORE_FILE): #check if high score is here
        try:
            with open(SCORE_FILE, "r") as file: #opens file in read mode
                for line in file #read each saved line
                    line = line.strip() #remove unneccessart spaces 
                    if not line:
                        continues #ignore emty line
                        part  = line.split("|") #separte saved info
                        if len(parts) == 4 
                            mode = part[0]
                            try:
                                score = int(parts[1])
                                player = parts[2]
                                date = parts[3] #only load recognized difficulty mode
                                
                                if (
                                    best_scores[mode] is None
                                    or score > best_scores[mode]["score"]
                                 ):
                                     best_scores[mode] = {
                                         
                                         "score": score,
                                         "player": player,
                                         "date": date
                                         
                                     }   
                            except ValueError: #skips corrupted scores
                                continue
        except OSError:
            print("Oh, something went wrong could not read score file.")
    return best_scores

def save_best_score(best_scores):
    try: 
        with open(SCORE_FILE, "w") as file:
            for mode, information in best_scores.items():
                if information is not None:
                    score = information ["score"]
                    player = information["player"]
                    date = information ["date"]
        file.write(
            f"{mode}|{score}|{player}|{date}\n"
            )
        print("\nBest scores have been locked in!")
    except OSError:
        print("\nOh, something went wrong counld not save scores.")

def display_best_scores(best_scores):
    print("\n")
    print("="* 35)
    print("           Best Scores")
    print("="* 35)

    for mode, information in best_scores.items():
        print(f"\n{mode.upper()} MODE")
        if information is not NONE:
            print("Best Score:", information["score"])
            print("Player:", information["player"])
            print("Date:", information["date"])
        else
            print("No recorded scores yet.")
        
    print("="* 35)
    
def get_player_name():
    while True:
        name = input("\nEnter your name: ").strip
        if name:
            name = name.replace("|", "")
            
            return name
        else:
            print("Enter a valid name.")
            
def select_mode():
    display modes()
    while True:
        choice = input(
            "\nPick your level (1, 2, or 3):"
        ).strip()
            
        if choice in GAME_MODES:
             return GAME_MODES[choice]
             
        else:
         print(
                "Invalid selection! "
                "Please choose 1, 2, or 3."
            )

def get_valid_guess(minimum, maximum):
    while True:
        guess = input("\nEnter your guess:").strip()
        try:
            number = int(guess)
        except ValueError:
            print("\nfYI!")
            
            print(
                "Please enter only numbers!"
                "Letters and symbols are not allowed."
                )
                
                continue
            
            if number < minimum or number > maximun
            
                print("\nOut of Range!")
                
                print(
                    f"Please enter a number between"
                    f"{minimum} and {maximun}."
                )
                
                continue 
            
            return number


  
