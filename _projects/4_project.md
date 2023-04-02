---
layout: page
title: CPU
description: A CPU that runs actual RISC-V instructions, implemented in Logisim <br> 
# <br>
# <br>
img: assets/img/cpu/cpu.gif
importance: 3
category: Others
---

More infomration can be found @ [COMPSCI 61C](https://cs61c.org/sp23/projects/proj3/part-a/). Thanks my partner Yuanrui Zhu!

### **Arithmetic Logic Unit (ALU)**

Below is the list of ALU operations for you to implement, along with their associated ALUSel values. add is already made for you. You are allowed and encouraged to use built-in Logisim components to implement the arithmetic operations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cpu/alu.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### **Register File (RegFile)**

It contains 32 registers that can be written to and read from.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cpu/regfile.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### **Immediate Generator (1)**

Creating just enough of the CPU to execute the addi instruction

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cpu/imm.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### **Datapath**

Recall the five stages for executing an instruction:

* Instruction Fetch (IF)
* Instruction Decode (ID)
* Execute (EX)
* Memory (MEM)
* Write Back (WB)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cpu/datapath.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### **I-type Instructions**

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cpu/itype.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>