# 一、本周工作
1、规划自己的方向

2、深度图代码原理理解
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%8713.png)

# 二、方向分类
## 人脸图片
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%871.png)
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%872.png)

## 图片复原

图片去噪

![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%873.png)

图片去雨

![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%874.png)

图片去模糊

![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%875.png)

## 图像增强

![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%876.png)

## 目标检测
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%877.png)
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%878.png)

## 图片分割
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%879.png)

## 风格转换
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%8710.png)

## 学习路线
![Alt](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/%E5%9B%BE%E7%89%8712.png)


# 三、深度代码原理
``` 
import numpy
import rosbag
import cv2
import os
from sensor_msgs.msg import Image
from cv_bridge import CvBridge  #CvBridge是一个ROS库，提供ROS和OpenCV之间的接口
from cv_bridge import CvBridgeError
rgb_path = '/home/darren/darren_file/vedio_darren/around_ground/rgb/'# absolute path of extracted rgb images
depth_path = '/home/darren/darren_file/vedio_darren/around_ground/depth/'# absolute path of extracted depth images
bridge = CvBridge()
with rosbag.Bag('/home/darren/darren_file/vedio_darren/around_ground/around_the_flowerbed.bag', 'r') as bag:
    num = 1
    for topic,msg,t in bag.read_messages():
        
        if topic == "/zed2/zed_node/depth/depth_registered": 
        # 输入是图像消息，以及可选的编码
        # 32FC1 32位 float 1通道 opencv格式   
        # 
        # 
        # 
            cv_image = bridge.imgmsg_to_cv2(msg, '32FC1') 
            cv_image = cv_image * 255  

            # timestr = "%.8f" %  msg.header.stamp.to_sec() 
            # image_name = timestr + '.png'# an extension is necessary
            image_name = str(num) + '.png'
            cv2.imwrite(depth_path + image_name, cv_image)  


            with open('depth.txt', 'a') as depth_time_file:
            	depth_time_file.write(timestr+" depth/"+image_name+"\n")

        if topic == "/zed2/zed_node/left/image_rect_color": 
        #  CV_8UC3, color image with blue-green-red color order
        #  8位 无符号 3通道 
            cv_image = bridge.imgmsg_to_cv2(msg, "bgr8")
            timestr = "%.8f" %  msg.header.stamp.to_sec()
            image_name = str(num) + '.png'
            cv2.imwrite(rgb_path + image_name, cv_image)

            with open('rgb.txt', 'a') as rgb_time_file:
            	rgb_time_file.write(timestr+" rgb/"+image_name+"\n")
        num += 1

```

分析博客：

https://blog.csdn.net/peng_258/article/details/127432861


