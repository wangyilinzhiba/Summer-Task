P18

---
# 机器学习任务攻略

---

## Framework of ML:

![image-20230724003133293](image2/image-20230724003133293.png)

- Step 1: function with unknown

- Step 2: loss from training data
- Step 3: opitimization

θ代表所有的未知参数

![image-20230724015800933](image2/image-20230724015800933.png)

---

## General Guide

**决策树:**

![image-20230724020030100](image2/image-20230724020030100.png)

### Loss on training data is too large.

If loss on **training data** is large, the problem maybe is:

1. model bias
   - solution: make your model complex
2. optimization
   - solution: Next Lecture

#### Model Bias

![image-20230724020411094](image2/image-20230724020411094.png)

- model bias: the model is too simple.
- Solution: redesign your model to make it more flexible.
  - more features
  - deep learning(more neurons,layers)

#### Optimization Issue

![image-20230724020653246](image2/image-20230724020653246.png)

- Large loss not always imply model bias. There is another possibility...

#### Model Bias v.s.Optimization Issue

*怎么判断是哪一个导致的Loss太大了呢?*

![image-20230724020842101](image2/image-20230724020842101.png)

- Gaining the insights from comparison

  ![image-20230724021317101](image2/image-20230724021317101.png)

- Start from shallower networks (or other models),which are easier to optimize.

- lf deeper networks do not obtain smaller loss on **training data**,then there is optimization issue.

- example:![image-20230724021638192](image2/image-20230724021638192.png)

- solution: More powerful opitimization technology(next lecture)

---

### Loss on training data is small.

- If loss on **testing data** is large, the problem maybe is:
  1. overfitting
  2. mismatch

#### Overfitting

- Small loss on training data, large loss on testing data. Why?

##### An extreme example:

![image-20230724022447959](image2/image-20230724022447959.png)

##### 一般情况下也可能发生类似的事情: 

![image-20230724022947182](image2/image-20230724022947182.png)

##### The Solution of Overfitting 

1. 增加训练资料![image-20230724023607571](image2/image-20230724023607571.png)

- Data augmentation(数据增强)![image-20230724023616186](image2/image-20230724023616186.png)

2. constrained model(限制模型)

   ![image-20230724024735863](image2/image-20230724024735863.png)

   ***<u>you can do that to constrain model:</u>***

   - Less parameters, sharing parameters
   - Less features
   - Early stopping
   - Regularization
   - Dropout

   **如果限制模型太过火了就会回到model bias 问题**

   ![image-20230724024818138](image2/image-20230724024818138.png)

---



#### Bias-Coplexity Trade-off:

![image-20230724024952260](image2/image-20230724024952260.png)

The extreme example again:

![image-20230724025255676](image2/image-20230724025255676.png)

####  Cross Validation(交叉验证):

*测试集分为测试集和验证集*可以得到更低的loss

![image-20230724030313845](image2/image-20230724030313845.png)

##### How to split training set?

- N-fold Cross Validation(N-折交叉验证法)

  ![image-20230724030652143](image2/image-20230724030652143.png)

---

#### Mismatch 

- Your training and testing data have different distributions.

**Most HWs do not have this problem, except HW11**

增加资料无法解决mismatch问题

![image-20230724031211744](image2/image-20230724031211744.png)

---
