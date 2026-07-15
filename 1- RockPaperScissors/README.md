Rock - Paper - Scissors Game (C++)

📝 Description

A console-based Rock, Paper, Scissors game where the player competes against the computer for a chosen number of rounds. The program tracks scores across rounds, determines a winner, and changes console color based on the round result.

Built after Algorithms Level 2, using functions, enums, structs, and pass-by-reference — before studying OOP.

💡 Logic / Approach


Two enums represent the game choices (Stone, Paper, Scissor) and the round result (Player, computer, Draw).
Two structs hold the running scores and the display names for the winner.
RandomNumber() generates the computer's choice using rand().
Choice_Player() reads the player's input; Choice_MrComputerChoice() generates the computer's random choice.
Calculates_Round() compares both choices and updates the score struct (passed by reference).
ColorScreen() changes the console color depending on who won the round.
Print_Round() and Print_ScoreRoundsGame() handle all result formatting.
All_RoundResult() loops through the chosen number of rounds (1–10) and runs each round.
Game_Play() runs the whole game and asks if the player wants to play again.


🎮 How It Works


The player enters how many rounds to play (1–10).
Each round, the player picks Stone, Paper, or Scissor; the computer picks randomly.
The winner of the round is calculated and shown with a color change.
After all rounds, the final score and overall winner are displayed.
The player can choose to play again or end the game.


📥 Sample Input

Hi how many rounds do you want (1) to (10) :? 3
Enter Choice: 1
Enter Choice: 2
Enter Choice: 3

🛠️ Concepts Used


Functions & pass-by-reference (&)
enum
struct
rand() for randomization
system("color") for console styling