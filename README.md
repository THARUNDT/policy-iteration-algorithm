# POLICY ITERATION ALGORITHM
J
## AIM
The aim of this experiment is to implement the Policy Iteration Algorithm in Reinforcement Learning to determine the optimal policy and corresponding value function for a given environment. Policy Iteration combines iterative policy evaluation and policy improvement steps to achieve convergence towards an optimal policy.

## PROBLEM STATEMENT
In Reinforcement Learning, the agent interacts with an environment modeled as a Markov Decision Process (MDP).
The challenge is to find an optimal policy that maximizes the long-term cumulative reward.
Policy Iteration addresses this by:

Evaluating the value of a given policy (Policy Evaluation).
Improving the policy based on the evaluated value function (Policy Improvement).
Repeating these steps until the policy converges to the optimal policy.

## POLICY ITERATION ALGORITHM
# STEP 1:
Initialization

Initialize an arbitrary policy π and value function V(s).

# STEP 2:
Policy Evaluation

For the current policy π, compute the value function V(s) for all states until convergence.

# STEP 3:
Policy Improvement

Update the policy by choosing actions that maximize the expected return using the current value function.
# STEP 4:
Check for Convergence

If the policy does not change (π′ = π), then the policy is optimal and the algorithm terminates.
Otherwise, repeat steps 2 and 3.

## POLICY IMPROVEMENT FUNCTION
### Name: THARUN D
### Register Number: 212223240167
```
def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)

    for s in range(len(P)):
        for a in range(len(P[s])):
            for prob, next_state, reward, done in P[s][a]:
                Q[s][a] += prob * (reward + gamma * V[next_state] * (not done))

    new_pi = lambda s: {s: a for s, a in enumerate(np.argmax(Q, axis=1))}[s]

    return new_pi

```
## POLICY ITERATION FUNCTION
### Name: THARUN D
### Register Number: 212223240167
```
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
  pi=lambda s: {s:a for s, a in enumerate(random_actions)}[s]
  while True:
    old_pi={s: pi(s) for s in range(len(P))}
    V=policy_evaluation(pi,P,gamma,theta)
    pi=policy_improvement(V,P,gamma)
    if old_pi=={s:pi(s) for s in range(len(P))}:
      break
  return V,pi

```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy
![WhatsApp Image 2025-09-27 at 10 51 33_293e384f](https://github.com/user-attachments/assets/26f81ca5-0fbf-4d61-a928-aac9de87c318)
![WhatsApp Image 2025-09-27 at 10 51 32_1e2cb7a0](https://github.com/user-attachments/assets/4d0ca328-b4e5-4bcd-b150-8b652c0fe7bd)

### 2. Policy, Value function and success rate for the Improved Policy
![WhatsApp Image 2025-09-27 at 10 51 32_386fb625](https://github.com/user-attachments/assets/488cf610-908e-498d-a17a-7e1c6c870e9e)
![WhatsApp Image 2025-09-27 at 10 51 33_36e0f13b](https://github.com/user-attachments/assets/972ed28f-f573-45e0-9442-5b44518baff6)


### 3. Policy, Value function and success rate after policy iteration
![WhatsApp Image 2025-09-27 at 10 51 31_e06b1889](https://github.com/user-attachments/assets/782b1c71-3c0c-479e-88bc-c1feb30f4377)
![WhatsApp Image 2025-09-27 at 10 51 32_801b1ba2](https://github.com/user-attachments/assets/e684788f-6aa1-4dae-899a-9299a770f990)


## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.
