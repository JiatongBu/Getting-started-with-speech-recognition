# 语音处理入门
4月组队
食物声音识别建模流程
一、环境配置

由于环境配置上碰到了很多坑，配置思路是
1、先安装anaconda，配置好环境
2、根据电脑配置装需要的包
3、修改Jupyter notebook文件打开及保存路径（默认是在C盘），
    step1:打开Anaconda Prompt,执行：jupyter notebook --generate-config
    step2:根据输出的路径，找到jupyter_notebook_config.py这个文件，用记事本打开
    step3:创建要保存Jupyter notebook文件的文件夹，复制路径
    step4:在jupyter_notebook_config.py文件中的c.NotebookApp.notebook_dir = "E:\Jupyterfiles"加上该路径，同时取消语句最前面的“#”
    step5:在Jupyter notebook快捷方式右键属性，删除目标中的“ %USERPROFILE%”,点击应用，确定，关闭。

加载数据

1）训练数据：!wget http://tianchi-competition.oss-cn-hangzhou.aliyuncs.com/531887/train_sample.zip
2）测试数据：!wget http://tianchi-competition.oss-cn-hangzhou.aliyuncs.com/531887/test_a.zip
明确建模目的

根据训练集中的音频数据所属的类别建立分类模型，并对测试集中的音频数据进行分类预测
可能采用的分类模型

支持向量机/随机森林/卷积神经网络等（本次采用CNN模型）
安装所需要的库

    !pip install tensorflow --user
    tensorflow的安装需要和python版本相匹配，一般直接都安装最新版的吧，可以省下好多麻烦
    2）!pip install librosa --user
    安装音视频处理库librosa，用于对音频数据进行处理提取特征

加载建模所需的库

import pandas/numpy/sklearn/tensorflow/librosa/glob/librosa.display/tqdm
建模流程

特征提取——划分数据集（训练集和测试集）——训练模型——模型用于预测——训练模型准确度及模型泛化能力的评估
