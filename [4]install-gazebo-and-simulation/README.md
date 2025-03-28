### 🚀 **Hướng Dẫn Cài Đặt & Mô Phỏng Robot với Gazebo trong ROS Noetic**  

Gazebo là một công cụ mô phỏng mạnh mẽ cho robot, được tích hợp chặt chẽ với ROS. Bài hướng dẫn này sẽ giúp bạn cài đặt Gazebo, kiểm tra mô phỏng cơ bản và thêm robot vào môi trường ảo.  

---

## 🔧 **1. Cài Đặt Gazebo & Các Gói Cần Thiết**  
Trước tiên, cập nhật hệ thống và cài đặt các gói cần thiết cho ROS Noetic:  
```bash
sudo apt update
sudo apt install ros-noetic-gazebo-ros ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control
```  
Sau đó, source ROS để đảm bảo các lệnh hoạt động chính xác:  
```bash
source /opt/ros/noetic/setup.bash
```  
Kiểm tra phiên bản Gazebo:  
```bash
gazebo --version
```  
🚀 **Kết quả mong đợi:** Một cửa sổ trống của Gazebo xuất hiện.  

---

## 🏗 **2. Kiểm Tra Mô Phỏng Cơ Bản với Gazebo**  
Chạy một môi trường trống trong Gazebo bằng lệnh:  
```bash
roslaunch gazebo_ros empty_world.launch
```  
🚀 **Kết quả mong đợi:** Gazebo khởi động với một môi trường trống.  

---

## 🐢 **3. Mô Phỏng TurtleBot3 trong Gazebo**  
### 🔹 **Cài đặt TurtleBot3**  
```bash
sudo apt install ros-noetic-turtlebot3-gazebo
```  
### 🔹 **Chạy mô phỏng TurtleBot3**  
```bash
export TURTLEBOT3_MODEL=burger
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```  
🚀 **Kết quả mong đợi:** Một robot TurtleBot3 xuất hiện trong Gazebo.  

### 🔹 **Điều khiển TurtleBot3 bằng bàn phím**  
```bash
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```  
 **Gói `turtlebot3_teleop` chưa được cài đặt**  
Chạy lệnh sau để cài đặt:
```bash
sudo apt install ros-noetic-turtlebot3-teleop
```
📌 **Sử dụng các phím mũi tên để di chuyển robot.**  

---

## 📡 **4. Kiểm Tra ROS Topic giữa ROS và Gazebo**  
### 🔹 **Liệt kê các topic đang hoạt động**  
Mở một terminal mới và nhập:  
```bash
rostopic list
```  
🚀 **Kết quả mong đợi:** Bạn sẽ thấy danh sách topic như:  
```
/cmd_vel  
/odom  
/joint_states  
```  
### 🔹 **Xuất dữ liệu vị trí của robot**  
```bash
rostopic echo /odom
```  
### 🔹 **Gửi lệnh di chuyển cho TurtleBot3**  
```bash
rostopic pub /cmd_vel geometry_msgs/Twist '{linear: {x: 0.5, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.5}}' -r 10
```  
🚀 **Kết quả mong đợi:** TurtleBot3 di chuyển trong Gazebo.  

---

## 🤖 **5. Thêm Robot Tùy Chỉnh vào Gazebo**  
Bạn có thể tạo một robot đơn giản bằng **URDF (Unified Robot Description Format).**  

### 🔹 **Tạo một package mới cho robot**  
```bash
cd ~/catkin_ws/src
catkin_create_pkg my_robot_description urdf rospy
```  
### 🔹 **Tạo tệp mô tả robot (`robot.urdf`)**  
Mở file `robot.urdf` trong thư mục `my_robot_description` và thêm nội dung sau:  
```xml
<?xml version="1.0" ?>
<robot name="my_robot">
  <link name="base_link">
    <visual>
      <geometry>
        <box size="0.5 0.5 0.5"/>
      </geometry>
      <material name="blue">
        <color rgba="0.0 0.0 1.0 1.0"/>
      </material>
    </visual>
  </link>
</robot>
```  
### 🔹 **Load robot vào Gazebo**  
```bash
roslaunch gazebo_ros empty_world.launch
rosrun gazebo_ros spawn_model -file ~/catkin_ws/src/my_robot_description/robot.urdf -urdf -model my_robot
```  
🚀 **Kết quả mong đợi:** Một khối hộp màu xanh xuất hiện trong Gazebo.  

---