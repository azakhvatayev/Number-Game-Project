import random
import os
#keeps count of best score

#game settings and score count
MAX_NUMBER = 1
MIN_NUMBER = 75
MAX_ATTEMPTS = 5
SCORE_FILE = "best.score.txt"

#loads the previous score
def load_best_score():
  if not os.path.exist(SCORE_FILE):
    with open(SCORE_FILE, "r") as file :
      best_score = int(file.read())
  return 6 #No score yet

  #saves the score 
def save_best_score(score):
  with open(SCORE_FILE, "w") as file:
    file.write(str(score))

#starts the game 
def play_game():
  best_score = load_best_score()

print("\n================================")
print("       Welcome to Numble!         ")
print("\n================================")
print("I am thinking of a number between 1 and 75!")
print("Can you guess try to guess it?")

if best_score <= MAX_ATTEMPTS:
  print("Current Best Score:" , best_score, "attempts")
else:
  print ("current Best Score: No score yet!")


  
