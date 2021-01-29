## Count-mAP：Map计算所需文件的生成在Keras当中的实现
---

## 目录
1. [所需环境 Environment](#所需环境)
2. [文件下载 Download](#文件下载)
3. [使用方式 Usage](#使用方式)

## 所需环境
tensorflow-gpu==1.13.1  
keras==2.1.5  

## 文件下载
ssd的h5权重文件  
链接: https://pan.baidu.com/s/1VOD35bbShx25n6LTpvBPGQ 提取码: zn3e  

大家要注意我例子中的VOC虽然写的是2007，但是实际上是2012的……  
链接: https://pan.baidu.com/s/1jLW5k65lP8hZJhguH6ELQQ 提取码: 4r3g  

## 使用方式
所有目标检测库都已经配备了对应的mAP的计算程序，直接按照步骤运行即可。    
博客链接：https://blog.csdn.net/weixin_44791964/article/details/104695264       
1. 准备好自己的测试集，测试集的设置一般有两个方法，一是在整个模型训练前，设置trainval_percent的大小进行分割，trainval_percent=0.9代表10%的数据用于测试；二是在训练前将测试集和训练集完全分开，当完成训练后，将训练集剪切走，将测试集复制进VOC2007中，此时将trainval_percent=0，代表当前VOC2007里面所有的数据用于测试。   
2. 在完成测试集的准备后，运行voc2ssd.py生成对应的test.txt文件。   
3. 修改ssd.py当中的model_path以及classes_path使其对应自己的模型。  
4. 运行get_dr_txt.py文件生成预测结果对应的txt。  
5. 运行get_gt_txt.py文件生成真实框对应的txt。  
6. 运行get_map.py文件获得网络的mAP值即可。  
