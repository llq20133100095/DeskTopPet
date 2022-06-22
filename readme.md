# 定制你的宠物桌面

最近想要做一个自己独一无二的桌面宠物，可以直接使用python来自己订制。属于一个小项目，这个教程主要包含几个步骤：

1. 准备需要的动图素材

2. 规划自己需要的功能

3. 使用python的PyQt5订制功能

在这个教程中，我主要实现了桌面宠物的几个功能：

1. 每隔一段时间切换动图素材+文字
2. 点击宠物时有额外动作
3. “故事大会”功能：跟宠物聊天，进行文本生成
4. “休息一下”功能：隔一个小时提醒你休息功能

话不多说，让我们开始把。

# 1. 准备需要的动图素材
这些素材你可以直接从网上下载找到，比如可以去动图素材网站：
[https://www.soogif.com/](https://www.soogif.com/)

![图 2](images/da746f9a59ddeae9a6f13a492403746fbf24e5e1df17e91860f6e5d9512d1d2f.png)  

搜索我要的动图“皮卡丘”，下载之后就需要对素材的背景去掉，设置成透明状态。

## 1.1 去除动图背景
这里可以利用PS（也可以使用网页版PS）工具，对动图去除背景。首先把动图导入到PS中，得到如下所示：

![图 3](images/c2868a9a61dc660b2a4d577de40781b7dd7fdbb435ff92364cc1dc9033d45cf3.png)  


其中最右边时每一帧的图片，选中其中一个图片，然后点击显示眼睛按钮：

![图 4](images/ad1c943b125e8db5699bec753f0d342e3caad5ce504465f15a800bf1b7f7562d.png)  

然后利用魔棒工具

![图 5](images/26d1787641302459850eeccb11a346fb1865bb2436a2cc47096019c28513217e.png)  

框选背景图，进行删除：

![图 6](images/134cfb9fc60e2687cdfa24df27b7251034b6256e8322ec10a301fb30c2775938.png)  


重复上面操作，最后导出gif图就可以得到纯白背景的动图了。

![图 6](click/20220614223056.gif)  

# 2.python环境安装
这次功能上，还额外调用了hugging face模块中的文本生成功能，因此需要安装：
```
pip install huggingface
```

# 3.项目工程

![图 7](images/ecc5c4f9dd15358040a47cab9727dac34e15da6588b6d4101d4c67a395e6bee5.png)  

● main.py：整体功能函数

● dialog.txt：存放随机展示的文本

● pikaqiu：存放随机展示的动图

● talk_show.py：文本生成功能

这里具体介绍怎么使用huggingface导入文本生成模型。

打开huggingface官网：

[https://huggingface.co/](https://huggingface.co/)，然后点击Models，搜索训练好的中文生成模型

![图 8](images/9ea7c27611bb56e87ca69a35b17f76f029cc5a67aa12fe8016843c9cb7b3a7e3.png)  


例如我找到一个GPT中文预训练模型：

![图 9](images/5a1f646bd634e25aba4f946fab194cb044f365db06cc99b7b9dcb700209f155c.png)  


有两种方法导入，一种是直接利用hugggingface，它会直接下载模型，一种是利用git下载模型：

![图 10](images/b1cd449bb890cd27c444d99f84a3f8507df796606c0f04bc3af6df07062bae7c.png)  


下载模型后，仅仅需要几行代码，就可以导入模型生成文本：
```python
from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline 
tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-cluecorpussmall")
model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-cluecorpussmall")
text_generator = TextGenerationPipeline(model, tokenizer)
```

# 4.功能展示

● 每隔一段时间会变化动图和文字：

![图 11](./images/随机展示.gif)  


● 点击宠物时有额外动作

![图 12](./images/点击.gif)  

● “故事大会”功能：跟宠物聊天，进行文本生成

![图 13](./images/故事大会.gif)  

● “休息一下”功能：隔一个小时提醒你休息功能

![图 13](./images/休息.gif)  

这是目前项目的所有功能拉，有兴趣的可以下载原代码进行订制属于你的桌面宠物。

这是项目地址：
[https://github.com/llq20133100095/DeskTopPet](https://github.com/llq20133100095/DeskTopPet)

我是leo，我们下期再见~



