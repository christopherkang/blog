---
layout: post
title: 'Modeling Mahjong'
date: 2021-03-26 01:01:01
published: true
---

My family - they *love* Mahjong. And not in a gossipy

## Mahjong & Assumptions
Mahjong is a zero-sum game - the tokens you earn directly follow from someone else's losses. There are four players, and typically an entire "game" takes place over multiple rounds. Our first assumption is that:
- The overall game of Mahjong will be modeled, versus modeling individual rounds

This was made primarily because available data only recorded game-level data. Second, the dynamics of mahjong is related pretty heavily to seating order - plays move counterclockwise and only some discarded tiles can be "eaten" by the person to immediately follow. We simplify this by assuming: 
- Data is drawn uniformly from all potential seating arrangements


## Model
Call $p_i \sim \mathcal{D}_i$ to be the skill of person $i$ drawn from a specific distribution $\mathcal{D}_i$. Because Mahjong is a zero-sum game, the total winnings/losses must add to zero. So, take the reward for each player $r_i$ to be:

$$r_i = p_i - \overline{\mu}$$

Where $\overline{\mu}$ is the average skill level of all other players. This model is useful because it accounts for the inherent randomness of tiles provided and variability in player performance. It is also justifiable in the real world - in particular, if everyone is given a bad hand (all $p_i$ small), then the rewards would be comparable as if everyone had a good hand (all $p_i$ large). 

For the $\mathcal{D}_i$, we take this to be $\mathcal{N}(\mu_i, \sigma_i)$ for convenience. 