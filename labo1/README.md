# Pacman Laboratory - Rational Agents

![Python](https://img.shields.io/badge/Python-AI_Algorithms-3776AB?style=for-the-badge&logo=python&logoColor=white)

## Project Source

This laboratory is based on the UC Berkeley AI Pacman projects, adapted for the 4ALGL4A course at EPHEC (Academic Year 2024-2025). The original Berkeley project has been updated to use Python 3.

**Course:** Laboratoire 1 – Agents rationnels  
**Instructors:** R. Absil, P. Bettens, E. Falkenauer, C. Leignel, T. Nicodeme, N. Vansteenkiste  
**Original Source:** [UC Berkeley AI Pacman Project](https://ai.berkeley.edu/multiagent.html)

## Overview

This laboratory consists of implementing different types of rational agents for the Pacman game. These agents use artificial intelligence algorithms to efficiently navigate the maze, avoid ghosts, and eat all the pellets.

## Modified Files

The main work was done in the `multiAgents.py` file, which contains the following agent implementations:

- **ReflexAgent** - Improved evaluation function for reflexive decision-making
- **MinimaxAgent** - Complete implementation of the Minimax algorithm
- **AlphaBetaAgent** - Implementation of Minimax with alpha-beta pruning
- **ExpectimaxAgent** - Implementation of Expectimax for probabilistic opponents
- **betterEvaluationFunction** - Enhanced evaluation function for game states

## Implemented Agents

### ReflexAgent
An agent that evaluates each possible action based on the resulting game state. This evaluation takes into account:
- Ghost proximity (penalty for being too close)
- Food proximity (reward for being close)
- Rewards for eating food
- Special handling for scared ghosts

**Usage:**
```bash
python pacman.py -p ReflexAgent
python pacman.py -p ReflexAgent -l testClassic
python pacman.py -p ReflexAgent -l openClassic
```

### MinimaxAgent
An agent that uses the Minimax algorithm to anticipate several moves ahead, assuming that ghosts seek to minimize its score. The agent:
- Explores possible actions up to a defined depth
- Assumes ghosts act optimally against it
- Chooses the action that maximizes its minimum possible score

**Usage:**
```bash
python pacman.py -p MinimaxAgent -l minimaxClassic -a depth=4
python pacman.py -p MinimaxAgent -l smallClassic -a depth=3
```

### AlphaBetaAgent
An improvement of the Minimax agent that uses alpha-beta pruning to optimize search:
- Significantly reduces computation time
- Allows exploration of greater depths
- Maintains the same behavior as Minimax

**Usage:**
```bash
python pacman.py -p AlphaBetaAgent -a depth=3 -l smallClassic
python pacman.py -p AlphaBetaAgent -a depth=4 -l mediumClassic
```

### ExpectimaxAgent
An agent that assumes ghosts move randomly rather than optimally:
- Calculates the mathematical expectation (average) of scores for ghost actions
- Is less pessimistic than Minimax when facing non-optimal adversaries
- Takes more risks when advantageous

**Usage:**
```bash
python pacman.py -p ExpectimaxAgent -l minimaxClassic -a depth=3
python pacman.py -p ExpectimaxAgent -l mediumClassic -a depth=4
```

### Enhanced Evaluation Function
An advanced evaluation function that considers several factors:
- Distance to the nearest food
- Number of remaining pellets
- Ghost positions (normal and scared)
- Presence and proximity of power capsules

## Additional Command Line Options

### Common Parameters
- `-l LAYOUT` - Choose the maze layout (testClassic, smallClassic, mediumClassic, openClassic, minimaxClassic, etc.)
- `-a depth=N` - Set search depth for Minimax/AlphaBeta/Expectimax agents
- `-k N` - Set number of ghosts (default: varies by layout)
- `-g GHOSTTYPE` - Ghost behavior (RandomGhost, DirectionalGhost)
- `-f SEED` - Fix random seed for reproducible results
- `-n N` - Run N games in succession
- `-q` - Disable graphics (faster simulation)
- `--frameTime T` - Set frame time (use 0 for fastest simulation)

### Examples
```bash
# Run multiple games without graphics for testing
python pacman.py -p AlphaBetaAgent -l smallClassic -a depth=3 -n 10 -q

# Run with directional ghosts and fixed seed
python pacman.py -p MinimaxAgent -g DirectionalGhost -f 42

# Fast simulation with custom ghost count
python pacman.py --frameTime 0 -p ReflexAgent -k 2
```

## Project Structure

- `pacman.py` - Main game script with command-line interface
- `multiAgents.py` - **Your agent implementations (modified)**
- `game.py` - Game mechanics and rules
- `ghostAgents.py` - Ghost agent implementations
- `keyboardAgents.py` - Human player control
- `layout.py` - Maze layout loader
- `layouts/` - Directory containing maze layouts
- `graphicsDisplay.py` - Graphical interface (tkinter)
- `textDisplay.py` - Text-based interface
- `util.py` - Utility functions

## Help

For detailed help on all available options:
```bash
python pacman.py --help
```
