# FlappyAI

A Flappy Bird clone powered by a self-learning AI. The birds are controlled by neural networks trained using the **NEAT** (NeuroEvolution of Augmenting Topologies) algorithm — no human plays the game, the AI figures out how to survive on its own through evolution.

Built with Python, Pygame, and neat-python. Original game code by [Tech With Tim](https://github.com/techwithtim).

---

## How It Works

- A population of 20 birds starts each generation.
- Each bird has its own neural network with 3 inputs:
  - Bird's current Y position
  - Distance from bird to the top pipe gap
  - Distance from bird to the bottom pipe gap
- The network outputs a single value: jump or don't jump.
- Birds that survive longer and pass more pipes earn higher fitness scores.
- After all birds die, NEAT breeds the next generation using the best performers.
- Over successive generations the birds get progressively better at the game.

The on-screen display shows:
- **Score** — number of pipes passed in the current generation
- **Gens** — number of generations that have run so far
- **Alive** — number of birds still alive in the current generation

---

## Requirements

- Python 3.6 or higher (tested on Python 3.13)
- pip

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/legolasanti/FlappyAI.git
cd FlappyAI
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install pygame neat-python
```

> **macOS users:** If you have multiple Python versions installed, use `pip3` or `pip3.13` to match the Python version you will run the game with.

---

## Running the Game

```bash
python fly.py
```

> **macOS users with Python 3.13:**
> ```bash
> python3.13 fly.py
> ```

A window will open and the AI will start training immediately. You don't need to do anything — just watch the birds learn. Close the window at any time to stop.

---

## Project Structure

```
FlappyAI/
├── fly.py                  # Main entry point — game loop + NEAT training
├── flappy.py               # Standalone human-playable version (no AI)
├── config-feedforward.txt  # NEAT algorithm configuration
├── requirements.txt        # Python dependencies
└── imgs/                   # Game assets (bird, pipe, background, base)
    ├── bird1.png
    ├── bird2.png
    ├── bird3.png
    ├── pipe.png
    ├── bg.png
    └── base.png
```

---

## Configuration

The NEAT algorithm is configured in `config-feedforward.txt`. Key settings you can tune:

| Parameter | Default | Description |
|---|---|---|
| `pop_size` | 20 | Number of birds per generation |
| `fitness_threshold` | 100 | Fitness score at which training stops |
| `conn_add_prob` | 0.5 | Probability of adding a new connection |
| `node_add_prob` | 0.2 | Probability of adding a new node |
| `weight_mutate_rate` | 0.8 | Probability of mutating a connection weight |

---

## Troubleshooting

### `RuntimeError: Missing required configuration item`
Your version of neat-python requires parameters to be explicitly set. Make sure your `config-feedforward.txt` contains all required fields. The version in this repository is up to date and includes all required parameters.

Pull the latest version:
```bash
git pull origin master
```

### `ModuleNotFoundError: No module named 'pygame'` or `No module named 'neat'`
Install the dependencies:
```bash
pip install -r requirements.txt
```

### Game window doesn't open on macOS
Try running with the full Python path:
```bash
python3.13 fly.py
```
If the window appears but is unresponsive, click on it once to bring it into focus.

---

## License

This project is for educational purposes. Game assets and original structure by [Tech With Tim](https://github.com/techwithtim/NEAT-Flappy-Bird).
