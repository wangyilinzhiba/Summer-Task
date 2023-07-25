P14

---
## 反向传播

# Gradient Descent

![image-20230723195924517](imageBP/img_1.png)

---

#### Chain Rule(链式法则)

![image-20230723200951331](imageBP/img.png)

现在回到Backpropagation,先考虑某一个neuron:

![image-20230723201342732](imageBP/image-20230723201342732.png)

![image-20230723222347633](imageBP/image-20230723222347633.png)

Forward pass: 计算出所有的 **∂z/∂w** 

Backward pass: 对所有的激活函数输入的z计算出所有的 **∂c/∂z** 

最后得到 **∂C/∂w = ∂z/∂w * ∂C/∂z**

---

####  Backpropagation -Forward pass

![image-20230723222922793](imageBP/image-20230723222922793.png)

![image-20230723222941184](imageBP/image-20230723222941184.png)

---

#### Backpropagation - Backward pass

![image-20230723223122885](imageBP/image-20230723223122885.png)

##### ∂c/∂z' 和∂c/∂z'' 怎么算呢, 假设他们已经算出来了

![image-20230723223334301](imageBP/image-20230723223334301.png)

从另外一个视角看待这个式子:

![image-20230723223404685](imageBP/image-20230723223404685.png)

##### 那如何算出∂C/∂z'和∂C/∂z''呢?

![image-20230723223536472](imageBP/image-20230723223536472.png)

###### Case 1. Output Layer

![image-20230723223648361](imageBP/image-20230723223648361.png)

###### Case 2. Not Output Layer

######  溯源到output layer![image-20230723223825444](imageBP/image-20230723223825444.png)

###### actually operation: 

![image-20230723223933088](imageBP/image-20230723223933088.png)

###### 从z5, z6 开始算往前传递:

![image-20230723224141642](imageBP/image-20230723224141642.png)

###### 建立反向的神经网络:

![image-20230723224258339](imageBP/image-20230723224258339.png)

##### Summary:

![image-20230723224609970](imageBP/image-20230723224609970.png)

### **∂C/∂w = ∂z/∂w * ∂C/∂z**



