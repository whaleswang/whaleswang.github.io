---
layout: post
title: 线性回归、神经网络、机器学习
---
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    extensions: [
      "MathMenu.js",
      "MathZoom.js",
      "AssistiveMML.js",
      "a11y/accessibility-menu.js"
    ],
    jax: ["input/TeX", "output/CommonHTML"],
    TeX: {
      extensions: [
        "AMSmath.js",
        "AMSsymbols.js",
        "noErrors.js",
        "noUndefined.js",
      ]
    }
  });
</script>

<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<br/>
本文将从一个简单的线性回归例子开始，让你逐步了解神经网络和机器学习的概念。

### 线性回归（Linear Regression）
<br/>
相信在中学时期大部分人都见过以下类似的“应用题”。

在研究硝酸钠的可溶性程度时，对不同的温度观测它在水中的溶解度，得观测结果如下，

<center>
![_config.yml]({{ site.baseurl }}/images/01lr/b1.png)
<br/>表格1</center>

求变量x与y的线性回归方程。

如何求解？首先，我们需要画一个散点图：

<center>
![_config.yml]({{ site.baseurl }}/images/01lr/1.png)
<br/>图1</center>

这时候如果问你，温度x取100的时候溶解度y是多少，你大概可以很快给一个近似的答案：160左右。一个简单的方法是画一条直线尽可能靠近所有点，在x=100的位置得到y，

![_config.yml]({{ site.baseurl }}/images/01lr/2.png)
<center>图2</center>

上述方法虽然易于理解和实施，但是它至少有两个缺点：
1. 无法得到相对精确且稳定的数值，不同的人可能得到不同的结果。2. 难以推广到多变量的情形。比如溶解度y不仅跟温度x1有关，还跟压强x2有关，此时我们要求解的是y和x1、x2的关系，我们需要画一个平面。假如继续增加变量（比如1000个），将超出人类视觉感知所能处理的范围。接下来，我们用另一个方法来求解，它包含以下几个步骤：
1. 假设y=ax + b2. 将表格中的x值代入1)中的方程，得到一系列代数表达式：[b, 10a + b, 20a + b, 50a + b, 70a + b]，我们称之为“预测值”3. 求解a和b，使得预测值和实际测量值（即表格中的y值）“最接近”以上步骤如果你觉得很简单，那么我想恭喜你，你已经掌握了“神经网络”的基本方法！我们来仔细思考每一步骤背后的含义。关于 y = ax + b。为什么我们会做如此假设？因为我们通过观察散点图，猜测y和x最有可能是“直线关系”。但这不是唯一可能正确的假设，我们还可以假设它们满足“曲线关系”，图3。事实上，我们可以用一些技巧让算法自动选择最适合的假设（或者模型），将在后续的文章探讨。![_config.yml]({{ site.baseurl }}/images/01lr/3.png)
<center>图3</center>
关于“预测值”。仔细想想，我们其实有一些“乐观”，因为我们认为我们可以通过任意的x预测y。事实上我们给出y = ax + b的假设的同时，已经做了另一个假设：x与y之间存在某种必然联系，并且这种联系就隐含在已知的测量数据中。这里提出“假设的假设”的思考，只是想说明所有结论都有作为其基础的假设，因此我们在必要的时候，可以对结论或其假设作出调整或提出质疑。关于“最接近”。回顾之前的步骤，我们有一系列已知的测量值，如表格1。然后，我们提出一个合理的假设y = ax + b，因此我们得到另一个表格：
<center>
![_config.yml]({{ site.baseurl }}/images/01lr/b1.png)
<br/>表格2</center>
显然，我们希望找到a, b的值，使得测量值y尽可能接近预测值yp，也就是让它们的“距离”足够的小，对于距离的一种自然的表达，

$$L= \sum_{i=1}^{n} x_{i} (y^{(i)}-yp^{(i)})^2$$


