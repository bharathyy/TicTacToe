# Tic-Tac-Toe Reinforcement Learning


This is a Python implementation of a Tic-Tac-Toe game where two players (Player 1 and Player 2) compete against each other. The game leverages reinforcement learning, allowing Player 1 to learn optimal strategies through self-play. The learning process is based on value iteration, with states being assigned values and updated based on the outcomes of games.

## Requirements
Python 3.x

NumPy

Pickle 

## Installation
To run the code, you'll need to install the necessary dependencies. You can install NumPy via pip:

## How It Works
Components
State Class: Manages the Tic-Tac-Toe board, checks for winners, and tracks the game state. It also handles rewards and resets the board after each round.
Player Class: Represents a player in the game, which can be an AI or a human. The AI uses an epsilon-greedy strategy for action selection and updates the state values during training.
HumanPlayer Class: Represents a human player who manually inputs actions through the terminal.
Training: The AI is trained through self-play, where two instances of the Player class compete against each other.
Play with Human: After training, you can play against the AI by running the play2 function, where Player 1 is the trained AI and Player 2 is a human player.
## Game Flow
Training Phase:

During training, two AI players (p1 and p2) compete against each other for a specified number of rounds.
After each game, the AI updates its state values based on the result (win, lose, or draw) and continues to improve its strategy.
Playing Against AI:

Once the AI has been trained, you can play against it by running the play2 function. The AI uses its learned policy to choose the best actions while the human player inputs their moves manually.
Methods
State Class:

getHash(): Generates a unique hash for the current board state.
winner(): Checks for a winner or tie and returns the result.
availablePositions(): Returns a list of available positions on the board.
updateState(position): Updates the board with the player's move.
giveReward(): Assigns rewards to the players based on the game outcome.
reset(): Resets the board to its initial state.
play(rounds): Trains the AI by letting the two players compete for a given number of rounds.
play2(): Allows a human to play against the trained AI.
Player Class:

chooseAction(positions, current_board, symbol): Selects the next action using an epsilon-greedy strategy.
addState(state): Records the current state for learning.
feedReward(reward): Updates the state values based on the outcome.
reset(): Resets the player's state for a new game.
savePolicy(): Saves the player's learned policy to a file.
loadPolicy(file): Loads a previously saved policy.
HumanPlayer Class:

chooseAction(positions): Prompts the human player to input their move.
Running the Code
1. Training the AI:
To train the AI players, run the following code:

    p1 = Player("p1")
    p2 = Player("p2")
    st = State(p1, p2)
    print("training...")
    st.play(50000)  # Train for 50,000 rounds
    p1.savePolicy()
2. Playing Against the AI:
After training, you can play against the trained AI:

    p1 = Player("computer", exp_rate=0)  # Set exploration rate to 0 for deterministic behavior
    p1.loadPolicy("policy_p1")  # Load the trained policy
    
    p2 = HumanPlayer("human")
    
    st = State(p1, p2)
    st.play2()
3. Customization
Training Rounds: You can modify the number of training rounds in the play() method.
Exploration Rate: Adjust the exp_rate parameter in the Player class to control the exploration vs. exploitation trade-off during training.
Output
During training, the progress is printed every 1,000 rounds. When playing against the AI, the board is displayed after every move, showing the current state of the game.


## Notes
The AI uses reinforcement learning with an epsilon-greedy strategy. It explores random moves occasionally and learns from the outcomes.
The trained AI can be loaded from a file to play against a human player.

## I refered https://github.com/MJeremy2017/reinforcement-learning-implementation/ which was helpful for me to understand. For more problems you can refer that as well

### Code By Bharathi Shankar J
