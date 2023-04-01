---
layout: page
title: Human-AI Collaboration
description: Learning Human Advice Giving to Improve Machine-Generated Advice Taking
img: assets/img/hai/hai.gif
importance: 4
category: Research
---

More information can bde found @ [GitHub](https://github.com/Thunderbeee/hai-cooking)

### **Overview**

Research has shown that people are generally receptive to receiving advice and will try to incorporate it into their decision-making. However, the level of adoption depends on their subjective judgment of how important the advice is, which is shaped by their prior experience and evaluation. As AI and recommendation systems become increasingly prevalent, humans are also receiving advice from machines. However, studies have shown that humans have an aversion to machine-generated advice or algorithm aversion, preferring advice from humans even when machines outperform humans. This is because mistakes made by machines are perceived to be much worse than humans' mistakes, leading to a loss of trust in machines. In a recent study, researchers found that despite algorithmic tips performing better than alternatives in helping people improve their performance, people were less likely to adopt them if they were counterintuitive compared to more intuitive human-provided tips.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/hai/first.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>

Our primary research questions focus on whether individuals are more likely to follow advice that is similar to their own advice, and if so, whether it is possible to learn an advice-giving style based on the behavioral data of how humans make sequential decisions and learn over time. To address these questions, we propose a unique approach where we learn humans' advice-giving style and use the same style when providing them with advice. Through an analysis of the qualitative responses obtained from a large-scale behavioral experiment conducted in Anonymized (2021), we have been able to identify two dimensions that characterize humans' advice-giving strategies: the content of the advice and its structure or style. We have developed several models using Transformer and long short-term memory (LSTM) models to predict the advice-giving style based on sequences of human users' actions throughout the game. We have demonstrated the effectiveness of these models in predicting and modifying human users' behavior.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/hai/second.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>

Initially, we discovered that there are significant differences in the way human users learn and perform prior to receiving guidance, which emphasizes the diversity among individuals. However, users' strategies became more aligned after being advised, either by a machine or by previous users. Even for those who didn't adhere to the guidance provided, their strategy changed, and the suggested advice for future users indicates that the advice had an impact on their approach. Furthermore, we noted that human users are more likely to comply with advice that is similar to their advice-giving style. Our model for predicting humans' advice-giving style achieved a reasonable accuracy of 41.2% across four categories of advice, which is substantially better than the empirical breakdown of roughly 25% per category. Our findings and techniques can aid in the development of tailored and adaptable AI decision-making systems that can learn from the behavioral trace data of human advice-giving and -taking styles and support human decision-making in a personalized and adaptable way by emulating the same styles.


<div class="caption">
    All those reference pictures are from https://arxiv.org/abs/2108.08454 by Hamsa Bastani, Osbert Bastani, Wichinpong Park Sinchaisri
</div> 