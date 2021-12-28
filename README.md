--------------------2021/12/28
1.修改轻量级网络：

crnn/models/ltecrnn.py   为了更好支持ncnn 推理   剔除了nn.Linear 更换成conv2d, 不然要Pnnx 还是有不少折腾

2.
crnn/data/dataset.py
       添加数据 RotR函数 透视变换，
       读取  __getitem__   一个车牌多张图片读取修改 
       添加空字符序列
 
3.gregenplate 添加模拟产生车牌 蓝牌 新能源车牌  黄牌模拟生成 ；  reformat_CCPD 从ccpd 生成车牌



4  96ttonnx.py   生成crnn.onnx

5  crnn.onnx--->crnn.parma 优化的时候注意 

Permute                  Transpose_25             1 1 89 output 0=3    0=3 要修改啊


--------------------------------------------------------








# CRNN_pytorch

**文本识别分为两部分：文本定位与文本序列识别。这个repo主要是做的后者。**

这是一个基于CRNN的文本序列识别项目。

在300w+的中文数据集上训练之后,得到了0.95的精度.(整个label都预测正确才认为正确)

我还做了一个基于keras的项目：

https://github.com/Liumihan/CRNN_kreas

 个人认为keras对于新手来说更好上手，但是灵活性不够。所以自己又迁移到了pytorch上来。

#### File Description

| File                 | Description          |
| :------------------- | -------------------- |
| crnn/                | 模型相关             |
| crnn/data/part_300w  | 训练模型的数据集文件 |
| crnn/data/dataset.py | 数据集加载处理类     |
| crnn/models/crnn.py  | 模型文件             |
| crnn/trainer_weights | 训练好的权重文件     |
| crnn/config.py       | 配置文件             |
| crnn/utils.py        | 辅助函数             |
| train.py             | 训练模型程序         |
| evaluate.py          | 模型测试程序         |



#### 参考文献：

##### 论文：

CRNN：https://arxiv.org/abs/1507.05717

CTC：http://people.idsia.ch/~santiago/papers/icml2006.pdf

##### 博客：

CRNN：

https://zhuanlan.zhihu.com/p/43534801

CTC：

https://www.cnblogs.com/qcloud1001/p/9041218.html，

https://distill.pub/2017/ctc/

https://towardsdatascience.com/intuitively-understanding-connectionist-temporal-classification-3797e43a86c

训练数据集：

链接: https://pan.baidu.com/s/1MinLf7IJvIAKK80wWJWPKg 提取码: yjjn 

##### git：

https://github.com/Liumihan/CRNN-Keras

https://github.com/Liumihan/keras_ocr
