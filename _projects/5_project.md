---
layout: page
title: BYoW
description: A randomly generated labyrinth with an interactable avatar 
img: assets/img/byow/byow.gif 
importance: 3
category: fun
---

### **Overview**

 A 2D tile-based world exploration engine. By “tile-based”, we mean the worlds you generate will consist of a 2D grid of tiles. By “world exploration engine” we mean that your software will build a world, which the user will be able to explore by walking around and interacting with objects in that world. Your world will have an overhead perspective. As an example of a much more sophisticated system than you will build, the NES game “Zelda II” is (sometimes) a tile based world exploration engine that happens to be a video game. More information can be found @ [COMPSCI 61B](http://fa20.datastructur.es/materials/proj/proj3/proj3)

<br>

### **World Generation**

As mentioned above, the first goal of the project will be to write a world generator. The requirements for your world are listed below:

* The world must be a 2D grid, drawn using our tile engine. The tile engine is described in lab12.
* The world must be pseudorandomly generated. Pseudorandomness is discussed in lab 12.
* The generated world must include distinct rooms and hallways, though it may also include outdoor spaces.
* At least some rooms should be rectangular, though you may support other shapes as well.
Your world generator must be capable of generating hallways that include turns (or equivalently, straight hallways that intersect).
* The world should contain a random number of rooms and hallways.
* The locations of the rooms and hallways should be random.
* The width and height of rooms should be random.
* The length of hallways should be random.
* Rooms and hallways must have walls that are visually distinct from floors. Walls and floors should be visually distinct from unused spaces.
* Rooms and hallways should be connected, i.e. there should not be gaps in the floor between adjacent rooms or hallways.
* The world should be substantially different each time, i.e. you should not have the same basic layout with easily predictable features

<br>

### **Interactivity**

In the second phase of the project, you’ll add the ability for the user to actually interact with the world, and will also add user interface (UI) elements to your world to make it feel more immersive and informative.

The requirements for interactivity are as follows:

* The user must be able to control some sort of “avatar” that can moved around using the W, A, S, and D keys. Lab 13 covers how to include interactivity. By “avatar”, we just mean some sort of on screen representation controlled by the user. For example, in my project, I used an “@” that could be moved around.
* The avatar must be able to interact with the world in some way.
* Your system must be deterministic in that the same sequence of keypresses from the same seed must result in exactly the same behavior every time. Note that a Random object is guaranteed to output the same random numbers every time.
* In order to support saving and loading, your program will need to create some files in your proj3 directory (more details later in the spec and in the skeleton code). The only files you may create must have the suffix “.txt” (for example “savefile.txt”). You will get autograder issues if you do not do this.
* Optionally, you may also include game mechanics that allow the user to win or lose (see gold points below). Aside from these feature requirements, there will be a few technical requirements for your system, described in more detail below.

 <div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/byow/games.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>