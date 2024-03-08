---
season: winter
tags: probabilistic-model
---

https://www.youtube.com/watch?v=2iF9PRriA7w

markov process = states and transitions model with probabilistic transitions

some transitions occur stochastically ex. car, 0.2 proba of light traffic, 0.7 of medium traffic, 0.1 of traffic jam  

The goal is to minimise an objective function, or satisfy a specification (=goal + constraints)
The basic idea is to find the shortest path, but we have to take the probabilities into account
The solution, instead of a path, is a policy, i.e. a lookup table : if I am at this state, I will chose this transition. Possiblity of enriching with more info to reflect additional contraints (time of day, how many time I have already visited this state, etc.)

For that we compute the mean cost for a state by computing the sum of the products of probability of transition i * cost of the resulting state if transition i occurs. NB: We compute the cost of the resulting state recursively.

Adding hard constraints is more reflexive of the real world than using only average values 
Trip to work example: we want to minimize the time, but we also want to never arrive after 10am. This excludes the car, which has best average values but bad worst case scenario.

Markov process for language generation: given the current state (current word), every other word has a probability of appearing, computed on the training corpus.
2nd degree Markov chain: the state takes into account the previous word generated in addition to the current one.