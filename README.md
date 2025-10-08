<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name: NAVEEN KUMAR E                      </h3>
<h3>Register Number/Staff Id:  212224230181     </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)

<h1>Program</h1>

``` python
GRID_SIZE = 4
wumpus = (2, 2)
pit = (1, 2)
gold = (3, 3)

agent_pos = [0, 0]
score = 1000

def neighbors(x, y):
    for dx, dy in [(-1,0),(1,0),(0,-1),(0,1)]:
        nx, ny = x+dx, y+dy
        if 0 <= nx < GRID_SIZE and 0 <= ny < GRID_SIZE:
            yield (nx, ny)

def perceive(x, y):
    percepts = []
    if any((nx, ny) == pit for nx, ny in neighbors(x, y)):
        percepts.append('Breeze')
    if any((nx, ny) == wumpus for nx, ny in neighbors(x, y)):
        percepts.append('Stench')
    if (x, y) == gold:
        percepts.append('GOLD')
    return percepts

while True:
    percepts = perceive(agent_pos[0], agent_pos[1])
    if gold == tuple(agent_pos):
        print("\ncurrent location: GOLD")
        print("\nGOLD FOUND! You won....")
        print(f"Your score is: {score}")
        break
    elif pit == tuple(agent_pos) or wumpus == tuple(agent_pos):
        print("\ncurrent location: DEAD")
        print("\nYou died!")
        score = 0
        print(f"Your score is: {score}")
        break
    else:
        msg = " ".join(percepts) if percepts else "Safe"
        print(f"\ncurrent location: {msg}")

    print("\npress u to move up")
    print("press d to move down")
    print("press l to move left")
    print("press r to move right")
    move = input().lower()

    if move == 'u' and agent_pos[0] > 0:
        agent_pos[0] -= 1
    elif move == 'd' and agent_pos[0] < GRID_SIZE - 1:
        agent_pos[0] += 1
    elif move == 'l' and agent_pos[1] > 0:
        agent_pos[1] -= 1
    elif move == 'r' and agent_pos[1] < GRID_SIZE - 1:
        agent_pos[1] += 1
    else:
        print("Invalid move!")
    
    score -= 10
```

<h1>OUTPUT</h1>
<img width="967" height="622" alt="image" src="https://github.com/user-attachments/assets/d3bf7ce7-a009-43ce-bdba-ce8657505f18" />

<h1>RESULT</h1>

Thus, The wumpus problem executed in python using prepositional Logic successfully
