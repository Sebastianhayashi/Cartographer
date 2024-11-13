# 如何在 RevyOS 上部署 ROS2

1. 将 deb 源添加到 ros.list 文件：

```
echo "deb https://mirror.iscas.ac.cn/revyos/revyos-ros2/ revyos-ros2 main" | sudo tee /etc/apt/sources.list.d/ros.list
```

2. 更新:

```
sudo apt update
sudo apt upgrade
```

3. 安装完整 ROS 2 Humble 版本的桌面完整版：

```
sudo apt install ros-humble-desktop-full
```

4. 安装 `rosdep`：

```
sudo apt install python3-rosdep2
```

5. 修改 rosdep 配置文件 /etc/ros/rosdep/sources.list.d/20-default.list，将 20-default.list 中的所有内容删除，替换成如下：

```
https://raw.githubusercontent.com/revyos-ros/rosdistro/master/rosdep/base.yaml
https://raw.githubusercontent.com/revyos-ros/rosdistro/master/rosdep/python.yaml
https://raw.githubusercontent.com/revyos-ros/rosdistro/master/rosdep/ruby.yaml
```
6. 设置 ROS 2 环境：

```
source /opt/ros/humble/setup.sh
```

7. 更新 ROS2 依赖：

```
rosdep update
```

8. 安装 cartographer：

```
sudo apt install ros-humble-cartographer-ros
```