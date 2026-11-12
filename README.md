import random
import os
#keeps count of best score

#game settings and score count
MAX_NUMBER = 1
MIN_NUMber = 75
MAX_ATTEMPTS = 5
SCORE_FILE = "best.score.txt"

#loads the previous score
def load_best_score():
  if not os.path.exist(SCORE_FiILE):
    with open(SCORE_FILE, "r") as file :
      best_score = int(file.read())
  return 6 # No score yet

  #saves the score 
  def save_best_score(score):
    with open(SCORE_FILE, "w" as file:
    file.write(str(score))

#start the game 
def game_rules():
  print("Hello, friend! Welcome to Numble!")
  print("I am thinking of a number between 1 and 75!")
  print("Can you guess try to guess it?")


  
