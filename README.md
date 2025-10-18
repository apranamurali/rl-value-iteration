# VALUE ITERATION ALGORITHM

## AIM
To develop a Python program to find the optimal policy for the given MDP using the value iteration algorithm.

## PROBLEM STATEMENT
The FrozenLake environment in OpenAI Gym is a gridworld problem that challenges reinforcement learning agents to navigate a slippery terrain to reach a goal state while avoiding hazards. The environment is closed with a fence, so the agent cannot leave the gridworld. The agent must determine the best actions to take from each state to maximize its reward.

## VALUE ITERATION ALGORITHM
1.Initialize the value function for all states to zero.

2.Iterate until the values converge, meaning changes become very small.

3.For each state, evaluate all possible actions.

4.Estimate expected rewards by considering next states and their probabilities.

5.Update the value function by selecting the best action that maximizes future rewards.

6.Repeat the process until the value function stops changing significantly.

7.Extract the optimal policy by choosing the action that leads to the highest value for each state.

8.Ensure the agent follows the best possible path to maximize rewards.

9.Used in Markov Decision Processes (MDPs) where the environment is uncertain or stochastic.

10.Guarantees finding the optimal policy, making it useful in reinforcement learning applications.

## VALUE ITERATION FUNCTION
### Name:APARNA.M
### Register Number: 212223220008

```
def value_iteration(P, gamma=1.0, theta=1e-10):
    V = np.zeros(len(P), dtype=np.float64)
    # Write your code here
    while True:
        delta = 0
        for s in range(len(P)):
            v = V[s]
            # Calculate the value of each action in the current state
            q_s = np.zeros(len(P[s]))
            for a in range(len(P[s])):
                for prob, next_state, reward, done in P[s][a]:
                    q_s[a] += prob * (reward + gamma * V[next_state] * (not done))
            # Update the state value function with the maximum action value
            V[s] = np.max(q_s)
            delta = max(delta, abs(v - V[s]))

        if delta < theta:
            break

    # Extract the optimal policy
    pi = np.zeros(len(P), dtype=np.int64)
    for s in range(len(P)):
        q_s = np.zeros(len(P[s]))
        for a in range(len(P[s])):
            for prob, next_state, reward, done in P[s][a]:
                q_s[a] += prob * (reward + gamma * V[next_state] * (not done))
        pi[s] = np.argmax(q_s)

    return V, pi
```
    
## OUTPUT:
<img width="1837" height="371" alt="image" src="https://github.com/user-attachments/assets/a124452c-d883-456e-ab54-6a8c09a386c0" />




## OPTIMAL VALUE FUNCTION

<img width="1413" height="333" alt="image" src="https://github.com/user-attachments/assets/23ccd78e-4dbf-4fd4-9450-540c48a74763" />




## SUCCESS RATE


<img width="1815" height="88" alt="image" src="https://github.com/user-attachments/assets/eb270017-643d-4dfb-abe4-56bef528f5d3" />

## RESULT:

Thus, a Python program is developed to find the optimal policy for the given MDP using the value iteration algorithm.


