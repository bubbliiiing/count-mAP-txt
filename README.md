## Count-mAP：Map计算所需文件的生成在Keras当中的实现
---

### 目录
1. [所需环境 Environment](#所需环境)
2. [文件下载 Download](#文件下载)
3. [使用方式 Usage](#使用方式)

### 所需环境
tensorflow-gpu==1.13.1  
keras==2.1.5  

### 文件下载
ssd的h5权重文件  
链接: https://pan.baidu.com/s/1VOD35bbShx25n6LTpvBPGQ 提取码: zn3e  

大家要注意我例子中的VOC虽然写的是2007，但是实际上是2012的……  
链接: https://pan.baidu.com/s/1jLW5k65lP8hZJhguH6ELQQ 提取码: 4r3g  

### 使用方式
博客链接：https://blog.csdn.net/weixin_44791964/article/details/104695264  
参照博客会更清晰，博客有图片  

我们首先在这个github上下载绘制mAP所需的代码。  
https://github.com/Cartucho/mAP  
在这个代码中，如果想要绘制mAP则需要三个内容。分别是：  
detection-results：指的是预测结果的txt。  
ground-truth：指的是真实框的txt。  
image-optional：指的是图片，有这个可以可视化，但是这个可以没有。  
  
我们需要生成这三个内容，此时下载第二个库，这个是我拿我制作的ssd代码写的一个可以生成对应txt的例子。  
https://github.com/bubbliiiing/count-mAP-txt  
我们首先将整个VOC的数据集放到VOCdevikit中  
  
然后修改voc2ssd.py里面的trainval_percent，一般用数据集的10%或者更少用于测试，trainval_percent=0.9表示10%用于测试。如果大家放进VOCdevikit的数据集不是全部数据，而是已经筛选好的测试数据集的话，那么就把trainval_percent设置成0，表示全部的数据都用于测试。  
  
然后运行voc2ssd.py。  
此时会生成test.txt，存放用于测试的图片的名字。  
  
然后依次运行主目录下的get_dr_txt.py和get_gt_txt.py获得预测框对应的txt和真实框对应的txt。  
get_dr_txt.py是用来检测测试集里面的图片的，然后会生成每一个图片的检测结果，我重写了detect_image代码，用于生成预测框的txt。  
利用for循环检测所有的图片。  
  
get_dr_txt.py是用来获取测试集中的xml，然后根据每个xml的结果生成真实框的txt。  
利用for循环检测所有的xml。  

完成后我们会在input获得三个文件夹。  

此时把input内部的文件夹复制到mAP的代码中的input文件夹内部就可以了，然后我们运行mAP的代码中的main.py，运行结束后，会生成mAP相关的文件。  

最终结果生成在Result里面。  
