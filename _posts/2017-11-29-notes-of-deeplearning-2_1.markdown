---

layout:     post

title:      "Notes of DeepLearning 2_1"

subtitle:   " 深度学习的实践方面 "

date:       2017-11-29 09:37:00

author:     "Zz"

header-img: ""

catalog: false

tags:

    - deep learning

---




深度学习第二课第一周的笔记---深度学习的实践方面|




## 1. 训练、验证、测试集




* **训练集**(train set): 用训练集对算法或模型进行训练；




*  **验证集**(development set): 利用验证集或者又称为简单交叉验证集(hold-out cross validation set)进行交叉验证，选择出最好的模型；




* **测试集**(test set): 最后利用测试集对模型进行测试，获取模型运行的无偏估计。




### 小数据时代




如100、1000、10000，划分如下：




* 无验证集：70%:30%；




* 有验证集：60%:20%:20%。




### 大数据时代




但是在如今的大数据时代，对于一个问题，我们拥有的data的数量可能是百万级别的，所以验证集和测试集所占的比重会趋向于变得更小。




验证集的目的是为了验证不同的算法哪种更加有效，所以验证集只要足够大能够验证大约2-10种算法哪种更好就足够了，不需要使用20%的数据作为验证集。如百万数据中抽取1万的数据作为验证集就可以了。




测试集的主要目的是评估模型的效果，如在单个分类器中，往往在百万级别的数据中，我们选择其中1000条数据足以评估单个模型的效果。




* 100万数据：98%:1%:1%；




* 超百万数据：99.5%:0.25%:0.25%。




#### 注意




* 建议验证集要和训练集来自于同一个分布，可以使得机器学习算法变得更快；




* 如果不需要用无偏估计来评估模型的性能，则可以不需要测试集。




## 2. 偏差、方差




欠拟合(underfitting)：高偏差(high bias)；




过拟合(overfitting)：高方差(high variance)。




## 3. 机器学习基本方法




解决高偏差和高方差的方法。




* 是否存在high bias？

  + 增加网络结构，如增加隐藏层数目；

  + 训练更长时间；

  + 寻找合适的网络框架，使用更大的NN结构；




* 是否存在high variance？

  + 获取更多数据；

  + 正则化(regularization)；

  + 寻找合适的网络框架。 




## 4. 正则化(regularization)

利用正则化来解决High variance 的问题，正则化是在 Cost function 中加入一项正则化项，惩罚模型的复杂度。

### Logistic Regression

代价函数：
\\[J(w,b)=\dfrac{1}{m}\sum\limits_{i=1}^{m}l(\hat y^{(i)},y^{(i)})+\dfrac{\lambda}{2m}||w||_{2}^{2}\\]

上式为逻辑回归的L2正则化。

* L2正则化：$\dfrac{\lambda}{2m}||w||_{2}^{2} = \dfrac{\lambda}{2m}\sum\limits_{j=1}^{n_{x}} w_{j}^{2}=\dfrac{\lambda}{2m}w^{T}w$
* L1正则化：$\dfrac{\lambda}{2m}||w||_{1}=\dfrac{\lambda}{2m}\sum\limits_{j=1}^{n_{x}}|w_{j}|$

其中λ为正则化因子。

注意：lambda在python中属于保留字，所以在编程的时候，用“lambd”代表这里的正则化因子λ。

### Nerual Network

加入正则化项的代价函数： $$J(w^{[1]},b^{[1]},\cdots,w^{[L]},b^{[L]})=\dfrac{1}{m}\sum\limits_{i=1}^{m}l(\hat y^{(i)},y^{(i)})+\dfrac{\lambda}{2m}\sum\limits_{l=1}^{L}||w^{[l]}||_{F}^{2}$$
其中$||w^{[l]}||_{F}^{2}=\sum\limits_{i=1}^{n^{[l-1]}}\sum\limits_{j=1}^{n^{[l]}}(w_{ij}^{[l]})^{2}$，因为w的大小为\\((n^{[l]},n^{[l-1]})\\)，该矩阵范数被称为“Frobenius norm”




  

  

