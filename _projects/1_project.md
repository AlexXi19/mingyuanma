---
layout: page
title: Pac-Man
description: A semester-long course project of Pac-Man, involving A* search algorithm, MDP, RL, etc. <br> <br> 
img: assets/img/pacman/pacman_game.gif
importance: 3
category: Artifical Intelligence
---

### **Overview**

The Pac-Man projects were developed by [CS 188 Fall 2021](https://inst.eecs.berkeley.edu/~cs188/fa21/projects/) . They apply an array of AI techniques to playing Pac-Man. However, these projects don’t focus on building AI for video games. Instead, they teach foundational AI concepts, such as informed state-space search, probabilistic inference, and reinforcement learning. These concepts underly real-world application areas such as natural language processing, computer vision, and robotics.

We designed these projects with three goals in mind. The projects allow you to visualize the results of the techniques you implement. They also contain code examples and clear directions, but do not force you to wade through undue amounts of scaffolding. Finally, Pac-Man provides a challenging problem environment that demands creative solutions; real-world AI problems are challenging, and Pac-Man is too.

Note: this project is not written by me from scratch, skeleton code is provided by course staff. The project is composed by three parts: Search, Multiagent, and RL. 
   
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/pacman/maze.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/pacman/pacman_multi_agent.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/pacman/q-learning.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


##### **Search**

Students implement depth-first, breadth-first, uniform cost, and A* search algorithms. These algorithms are used to solve navigation and traveling salesman problems in the Pacman world.

##### **Multiagent**

Classic Pacman is modeled as both an adversarial and a stochastic search problem. Students implement multiagent minimax and expectimax algorithms, as well as designing evaluation functions.

##### **Reinforcement Learning**

Students implement model-based and model-free reinforcement learning algorithms, applied to the AIMA textbook’s Gridworld, Pacman, and a simulated crawling robot.
