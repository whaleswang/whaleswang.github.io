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
<br/>

求变量x与y的线性回归方程。

如何求解？首先，我们需要画一个散点图：

<center>
![_config.yml]({{ site.baseurl }}/images/01lr/1.png)
<br/>图1</center>

这时候如果问你，温度x取100的时候溶解度y是多少，你大概可以很快给一个近似的答案：160左右。一个简单的方法是画一条直线尽可能靠近所有点，在x=100的位置得到y，

![_config.yml]({{ site.baseurl }}/images/01lr/2.png)
<center>图2</center>

上述方法虽然易于理解和实施，但是它至少有两个缺点：


<center>图3</center>


![_config.yml]({{ site.baseurl }}/images/01lr/b1.png)
<br/>


$$L= \sum_{i=1}^{n} x_{i} (y^{(i)}-yp^{(i)})^2$$


