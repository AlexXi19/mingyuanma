---
layout: page
title: Image-Image Translation
description: Unpaired Image-to-Image Translation using Cycle-GAN with JAX framework.<br> <br> 
img: assets/img/cyclegan/cyclegan.gif
importance: 1
category: work
---
This is a team work! Thanks [Daniel Zou](https://dlzou.github.io), [Alex Xi](https://www.alexhxi.com), and [Runzhe Mo](https://github.com/hairlessdevil)! Check it out @ [cyclegan-jax](https://github.com/dlzou/cyclegan-jax)

<br>

### **Introduction**

In this project, we replicate the experiments in [Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks](https://junyanz.github.io/CycleGAN/) with the JAX framework and convert the key concepts to homework problems. The paper introduces [CycleGAN]((https://junyanz.github.io/CycleGAN/)), a variant of the traditional [GAN](https://arxiv.org/abs/1406.2661), that is aimed at the task of image-to-image translation. At a high level, this task involves learning a mapping G: X → Y to translate images in domain X to domain Y. Before CycleGAN, the status quo for image translation tasks was to use a set of aligned image pairs (x, y) for training. However, such paired and cleaned image datasets are often inaccessible or costly to create. CycleGAN introduces the concept of “cycle consistency” to eliminate the need for paired datasets so that any two sets of images, one set sampled from the distribution of X and the other from Y, can be used for training. This is highly beneficial for vision and graphics tasks where pairing such data is not feasible.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cyclegan/images.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### **Details**

If we were to simply train a GAN to learn a mapping G that translates from domain X to Y with an unpaired dataset, we cannot ensure that a generated “fake” Y image preserves any characteristics of the original X image, because there is nothing enforcing a one-to-one structure between the input and output. CycleGAN resolves this with the addition of the cycle consistency property; if we learn two mappings G: X → Y and F: Y → X which are inverses of each other, we can impose additional bijective structure on our model. In practice, this means CycleGAN trains two generators, one taking input in domain X then outputting in domain Y, and the other in the opposite direction. When the two generators are chained, we expect to get back the original image, i.e. F(G(X)) ≈ X and G(F(Y)) ≈ Y. This allows the model to translate images between the two domains while ensuring that not only are the resulting images realistic, but also some features of the original images are preserved. Therefore, two classes of objectives are used to train CycleGAN: [adversarial losses](https://arxiv.org/abs/1406.2661) make the images generated from the original domain resemble the data distribution of the target domain as in traditional GANs, and cycle consistency losses ensure that the learned maps G and F are mutual inverses so we no longer need paired datasets. To train the CycleGAN model, two GANs are trained simultaneously, alternating between updating the generators and updating the discriminators. In particular, generators are optimized using the two aforementioned objectives, while discriminators are trained using a combination of random real images from each domain and generated images from the other domain.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cyclegan/algorithm.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### **Epilogue**

Once trained, the CycleGAN model can perform the task of image translation between domains. This allows for a wide range of applications, such as converting photographs of horses to photographs of zebras or converting images of landscapes to cityscapes. For this project, our goal is to understand and reimplement CycleGAN's architecture, learn the fine-grained details of how it is best trained, then evaluate and interpret the model’s performance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cyclegan/paints.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    All above pictures are from original paper.
</div>

