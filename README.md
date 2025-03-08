# AI Application Practice

## gif
![프로젝트 데모1](./gif/gif1.gif)
![프로젝트 데모2](./gif/gif2.gif)
![프로젝트 데모3](./gif/gif3.gif)

## overview
The Running event in AI Olympics is a competitive environment where AI agents compete to reach the finish line faster than their opponent.

## Multi-Agent Game Evaluation Platform --- Jidi (及第)
Jidi supports online evaluation service for various games/simulators/environments/testbeds. Website: [www.jidiai.cn](www.jidiai.cn).

A tutorial on Jidi: [Tutorial](https://github.com/jidiai/ai_lib/blob/master/assets/Jidi%20tutorial.pdf)

## Navigation

```
|-- Competition_IJCAI2023                   // https://github.com/jidiai/Competition_IJCAI2023.git 
	|-- agents                          // Agents that act in the environment
	|	|-- random                  // A random agent demo
	|	|	|-- submission.py   // A ready-to-submit random agent file
	|-- env		                    // scripts for the environment
	|	|-- config.py               // environment configuration file
	|	|-- olympics_integrated.py  // The environment wrapper	
	|-- olympics_engine		    // Game engine (https://github.com/jidiai/olympics_engine)
	|-- rl_trainer                      // A training example of some of the sub-scenarios (for reference only)
	|-- utils               
	|-- run_log.py		            // run the game with provided agents (same way we evaluate your submission in the backend server)
```

---
## Dependency

>conda create -n olympics python=3.8.5

>conda activate olympics

>pip install -r requirements.txt

---

## Run a game

>python olympics_engine/main.py

---

## Game Rules
Two AI agents compete on a track.

The agent that reaches the finish line first wins.

An agent can also win by reducing the opponent's energy to zero.

### State
The environment provides state information in the following format:
state[agent_index]['obs']['agent_obs']
Represented as a 40x40 2D matrix.

Meaning of values:

Team 0: 10

Team 1: 8

Track: 6

Arrows: 4

Finish line: 7

### Actions
Agents can perform the following two actions:

Force: Adjust the acceleration of the car (-100 ~ 200)

Angle: Adjust the steering angle (-30 ~ 30)

### Rewards
Winning: +1

Otherwise: 0

### Environment Features
The track can have various shapes (circular, S-shaped, straight, etc.).

Agents must navigate obstacles and directional indicators to find the optimal path.

### Environment Rules
1. Each agent controls an elastic ball with the same mass and radius.

2. Agents can collide with each other or walls, potentially losing speed.

3. Each agent has a limited amount of energy, which is consumed based on applied force and displacement.

4. Energy regenerates at a fixed rate, but if it reaches zero, the agent can no longer apply force.

5. The game continues until all subgames are finished.

### Competition_IJCAI2023
source code for IJCAI 2023 Competition

### References
Refer to the official AI Olympics documentation to better understand the environment and optimize strategies.

Reinforcement learning and optimal pathfinding algorithms can be used to enhance performance.
