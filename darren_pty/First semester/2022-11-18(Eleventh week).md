# 一、本周工作
1、无人机轨迹圆的实现(``` 已实现 ```)

#  二、工作细节
## 2.1 仿真时正在运行的节点和话题关系图
```rqt_graph```
![rgb图](https://img-blog.csdnimg.cn/0c41b71e7eaa4d798f8770be29e84b83.png)

## 2.2 查看/uav1/prometheus/fake_rc_in话题输出 
```rostopic echo /uav1/prometheus/fake_rc_in```
![rgb图](https://img-blog.csdnimg.cn/c3290e0a876f48529faefe4b3233c785.png)

## 2.3 转换为相应的控制状态
![rgb图](https://img-blog.csdnimg.cn/415196f2eafa46899aa9ce6845a093cb.png)



## 2.4 更改仿真的launch文件 及 遥控器映射
(1)将PX4、Gazebo仿真及MAVROS 替换为 真机的MAVROS

(2)修改真实遥控器通道映射
![rgb图](https://github.com/ZJUT-IoCS-MAS/darren_pty/blob/main/1-UAV_SLAM_PRJ/1-pic/9.png)



## 2.5 真机圆轨迹视频

链接：https://www.bilibili.com/video/BV1S84y1k7RW/?spm_id_from=333.999.0.0&vd_source=88bceb64b89804ec0cf90b2e004bf688


# 三、存在的问题
## 3.1 未处理之前的仿真 circular_raw 

![rgb图](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/circular_raw.gif)
链接：https://www.bilibili.com/video/BV1hG4y147ZD/?vd_source=88bceb64b89804ec0cf90b2e004bf688 

## 3.2  更改后的仿真 circular

![rgb图](https://github.com/MOSEAA/ZYJ-Group/blob/main/darren_pty/pic(Ninth%20week)/circular.gif)

链接：https://www.bilibili.com/video/BV1ae4y1p76z/?vd_source=88bceb64b89804ec0cf90b2e004bf688 




## 3.3 但是圆轨迹精度不够，有时候不能形成回环

未形成回环链接： https://www.bilibili.com/video/BV1EK411d7mK/?vd_source=88bceb64b89804ec0cf90b2e004bf688

更改后形成回环链接：https://www.bilibili.com/video/BV1f44y1Q7Lx/?vd_source=88bceb64b89804ec0cf90b2e004bf688




