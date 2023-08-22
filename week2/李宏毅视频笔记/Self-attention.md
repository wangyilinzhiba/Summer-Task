# self-attention（自注意力机制）

---

### Sophisticated Input

- Input is a vector
- Input is a set of vectors 

![image-20230812121254638](Self-attention/image-20230812121254638.png)

#### Vector Set as Input

（词汇，音频，图片.)

##### 怎么把一个词汇表示成一个向量呢？

- One-hot Encoding

  ![image-20230812121410921](Self-attention/image-20230812121410921.png)

- Word Embedding

  ![image-20230812121429982](Self-attention/image-20230812121429982.png)

##### 一段声音信号其实是一个向量

叫做一个Frame。25ms。

1s -> 100frames,1f分钟就有6000个向量。

![image-20230812121837093](Self-attention/image-20230812121837093.png)

##### Graph（图） is also  a set of vectors.(consider each node as a vector)

![image-20230812122016421](Self-attention/image-20230812122016421.png)

![image-20230812122054522](Self-attention/image-20230812122054522.png)

---

### What is the output?

- Each vector has a label.

  ![image-20230812122247742](Self-attention/image-20230812122247742.png)

  词性标注，音标标注，等。

  ![image-20230812122535191](Self-attention/image-20230812122535191.png)

- The whole Sequence has a label.

  ![image-20230812124050443](Self-attention/image-20230812124050443.png)

  情感分析，语者辨认，分子毒性预测，等

  ![image-20230812124148229](Self-attention/image-20230812124148229.png)

- Model decides the number of labels itself（Seq2Seq）

  ![image-20230812124241344](Self-attention/image-20230812124241344.png)

---

### Sequence  Labeling

如果是Fully-connected network，直接输入的花没办法识别saw和saw的区别。

![image-20230812134722839](Self-attention/image-20230812134722839.png)

正确的做法是把前后几个向量叠加起来：

![image-20230812134814580](Self-attention/image-20230812134814580.png)

但是还是有局限:

- It is possible to consider the context?

  FC can consider the neighbor

- How to consider the whole Sequence?

  - a window covers the whole sequence?

![image-20230812192802915](Self-attention/image-20230812192802915.png)

## SELF-ATTENTION

将一整个sequence输入。输入几个vector就输出几个vector，这四个vector考虑一整个sequence才得到的。![image-20230812193102320](Selfattention.assets/image-20230812193102320.png)

self-attention可以叠加很多次：

![image-20230812193114315](Self-attention/image-20230812193114315.png)

可以将fully connected和self-attention 交替使用。

 ![image-20230812193332633](Self-attention/image-20230812193332633.png)

#### Self-attention是怎么运作的呢？

self-attention的input是一串的vector。

self-attention的output是另一串的vector。

![image-20230812193547018](Self-attention/image-20230812193547018.png)

如何产生b1向量呢？

- step1：根据a1找出这个sequence里面跟a1相关的向量。每一个向量跟a的关联度以α表示。Find the relevant vectors in a sequence。

- step2：

  1. 方法一（常用）：Dot-product。向量乘以两个不同的矩阵得到q，k再把q，k相乘再相加得到α。

     ![image-20230812194044693](Self-attention/image-20230812194044693.png)

  2. 方法二：additive 

     ![image-20230812194106500](Self-attention/image-20230812194106500.png)

- Step3：

  - ![image-20230812194303316](Self-attention/image-20230812194303316.png)

  -  ![image-20230812194423990](Self-attention/image-20230812194423990.png)

    

