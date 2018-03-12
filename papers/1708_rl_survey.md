# [A Brief Survey of Deep Reinforcement Learning](https://arxiv.org/abs/1708.05866)

##### TLDR - ESSENTIAL READING

**RL** *is a step towards building autonomous systems with a higher level understanding of the visual world*. **DL** *enables **RL** to scale to decision-making problems that were previously intractable.* Survey about last papers and current challenges in this field.

- Great article to check your knowledge of RL field or to start to understand it. All necessary theory such as MDP/POMDP and state/qvalue/policy functions included. 
- Really cool paper to confirm your PhD research proposals :)
- Lots of interesting links.

##### Highlights

MDP:

- A set of states *S*, plus a distribution of starting states p(s<sub>0</sub>).
- A set of actions *A*.
- Transition dynamics *T* (s<sub>t+1</sub>|s<sub>t</sub> , a<sub>t</sub> ) that map a state-action pair at time t onto a distribution of states at time t + 1.
- An immediate/instantaneous reward function *R*(s<sub>t</sub> , a<sub>t</sub> , s<sub>t+1</sub>).
- A discount factor *γ* ∈ [0, 1], where lower values place more emphasis on immediate rewards. 

RL challenges:

- The optimal policy must be inferred by **trial-and-error interaction** with the environment. The **only learning signal** the agent receives is the **reward**.
- The **observations** of the agent **depend on its actions** and can contain strong temporal correlations.
- Agents must deal with **long-range time dependencies**: Often the consequences of an action only materialise after many transitions of the environment. This is known as the (temporal) credit assignment problem [135].

Dynamic Programming:

- **SARSA** - *on-policy*, uses transitions generated by the behavioral policy: 
  Q<sup>π</sup>(s<sub>t</sub>, a<sub>t</sub>)  ← Q<sup>π</sup>(s<sub>t</sub>, a<sub>t</sub>)  + α [*r*<sub>t</sub> + *γ* Q<sup>π</sup>(s<sub>t+1</sub>, a<sub>t+1</sub>)  - Q<sup>π</sup>(s<sub>t</sub>, a<sub>t</sub>) ]
- **Q-learning** - *off-policy*, directly approximates Q<sup>*</sup>:
  Q<sup>π</sup>(s<sub>t</sub>, a<sub>t</sub>)  ← Q<sup>π</sup>(s<sub>t</sub>, a<sub>t</sub>)  + α [*r*<sub>t</sub> + *γ* *max*<sub>a</sub>Q<sup>π</sup>(s<sub>t+1</sub>, a)  - Q<sup>π</sup>(s<sub>t</sub>, a<sub>t</sub>) ]
- To find Q<sup>*</sup> from an arbitrary Q<sup>π</sup> , we use **generalised policy iteration**.

Policy Search:

- Perhaps the greatest advantage of gradient-free policy search is that they can also optimise non-differentiable policies.

Planning and Learning:

- **Model-free** RL methods learn directly from interactions with the environment, but **model-based** RL methods can simulate transitions using the learned model,
  resulting in **increased sample efficiency**. 

Value functions:

- The combination of the **duelling DQN with prioritised experience replay** is one of the state-of-the-art techniques in **discrete action** settings.
- **NAF** is one of several state-of-the-art techniques in **continuous control** problems [40].
- **Metz et al.** [81] used this idea in order to construct the sequential DQN,
  allowing them to discretise a large action space and **outperform NAF in continuous control problems**.

Policy Search:

- Recent work has reignited interest in **evolutionary methods** for RL as they can potentially be distributed at larger scales than techniques that rely on gradients [116].
- The combination of **TRPO** and **GAE** remains one of the state-of-the-art RL techniques in **continuous control.** Also **PPO** (w/ or w/o **GAE**).
- On-policy methods can be more stable, whilst off-policy methods can be more data efficient.

Current Research and challenges:

- Hierarchical RL and the discovery and generalisation of goals.
- Imitation learning and Inverse RL: *...generative adversarial imitation learning (GAIL) was later extended to allow IRL to be applied even when receiving expert trajectories from a different visual viewpoint to that of the RL agent [131].*
- Multi-agent RL: *...investigate the effects of learning and sequential decision making in game theory [48, 71].*
- Memory and attention: *...it is possible to add a differentiable memory to the DQN, which allows it to more flexibly process information in its “working memory” [96].*
- Transfer learning.

##### Afterworlds

Things to thing about:

- Meta learning.
- Multi-agent RL and self-play.
- Learning to remember (memory & attention).
- Imitation learning and Inverse RL & GANs.

##### Interesting links

5. [Dzmitry Bahdanau, Philemon Brakel, Kelvin Xu, Anirudh Goyal, Ryan Lowe, Joelle Pineau, Aaron Courville, and Yoshua Bengio. An Actor-Critic Algorithm for Sequence Prediction. In ICLR, 2017.](https://arxiv.org/abs/1607.07086)


7. [Nir Baram, Oron Anschel, and Shie Mannor. Model-Based Adversarial Imitation Learning. In NIPS Workshop on Deep Reinforcement Learning, 2016.](https://arxiv.org/abs/1612.02179)


29.  [Yan Duan, John Schulman, Xi Chen, Peter L Bartlett, Ilya Sutskever, and Pieter Abbeel. RL2 : Fast Reinforcement Learning via Slow Reinforcement Learning. In NIPS Workshop on Deep Reinforcement Learning, 2016.](RL2 : Fast Reinforcement Learning via Slow Reinforcement Learning)


40. [Shixiang Gu, Timothy Lillicrap, Ilya Sutskever, and Sergey Levine. Continuous Deep Q-Learning with Model-Based Acceleration. In ICLR, 2016.](https://arxiv.org/abs/1603.00748)
41. [Shixiang Gu, Timothy Lillicrap, Zoubin Ghahramani, Richard E Turner, Bernhard Schölkopf, and Sergey Levine. Interpolated Policy Gradient: Merging On-Policy and Off-Policy Gradient Estimation for Deep Reinforcement Learning. In NIPS, 2017.](https://arxiv.org/abs/1706.00387)


48. [Johannes Heinrich and David Silver. Deep Reinforcement Learning from Self-Play in Imperfect-Information Games. 2016.](https://arxiv.org/abs/1603.01121)


71. [Joel Z Leibo, Vinicius Zambaldi, Marc Lanctot, Janusz Marecki, and Thore Graepel. Multi-Agent Reinforcement Learning in Sequential Social Dilemmas. In AAMAS, 2017.](https://arxiv.org/abs/1702.03037)


78. [Yuxi Li. Deep Reinforcement Learning: An Overview. arXiv:1701.07274, 2017.](Yuxi Li. Deep Reinforcement Learning: An Overview)


81. [Luke Metz, Julian Ibarz, Navdeep Jaitly, and James Davidson. Discrete Sequential Prediction of Continuous Actions for Deep RL. arXiv:1705.05035, 2017.](https://arxiv.org/abs/1705.05035)


96. [Junhyuk Oh, Valliappa Chockalingam, Satinder Singh, and Honglak Lee. Control of Memory, Active Perception, and Action in Minecraft. In ICLR, 2016.](https://arxiv.org/abs/1605.09128)


98. [Emilio Parisotto and Ruslan Salakhutdinov. Neural Map: Structured Memory for Deep Reinforcement Learning. arXiv:1702.08360, 2017.](Neural Map: Structured Memory for Deep Reinforcement Learning)


105. [Alexander Pritzel, Benigno Uria, Sriram Srinivasan, Adrià Puigdomènech, Oriol Vinyals, Demis Hassabis, Daan Wierstra, and Charles Blundell. Neural Episodic Control. In ICML, 2017.](https://arxiv.org/abs/1703.01988)

106. [Marc’Aurelio Ranzato, Sumit Chopra, Michael Auli, and Wojciech Zaremba. Sequence Level Training with Recurrent Neural Networks. In ICLR, 2016.](https://arxiv.org/abs/1511.06732)


116. [Tim Salimans, Jonathan Ho, Xi Chen, and Ilya Sutskever. Evolution Strategies as a Scalable Alternative to Reinforcement Learning. arXiv:1703.03864, 2017.](https://arxiv.org/abs/1703.03864)


123.  [John Schulman, Philipp Moritz, Sergey Levine, Michael Jordan, and Pieter Abbeel. High-Dimensional Continuous Control using Generalized Advantage Estimation. In ICLR, 2016.](https://arxiv.org/abs/1506.02438)


131. [Bradley C Stadie, Pieter Abbeel, and Ilya Sutskever. Third Person Imitation Learning. In ICLR, 2017.](https://arxiv.org/abs/1703.01703)


150. [Harm Vanseijen and Rich Sutton. A Deeper Look at Planning as Learning from Replay. In ICML, 2015.](http://proceedings.mlr.press/v37/vanseijen15.pdf)


156. [Jane X Wang, Zeb Kurth-Nelson, Dhruva Tirumala, Hubert Soyer, Joel Z Leibo, Rémi Munos, Charles Blundell, Dharshan Kumaran, and Matt Botvinick. Learning to Reinforcement Learn. In CogSci, 2017.](https://arxiv.org/abs/1611.05763)
