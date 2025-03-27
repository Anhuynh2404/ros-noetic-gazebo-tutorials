Dưới đây là phiên bản được trình bày lại một cách logic, dễ đọc và chuyên nghiệp hơn:  

---

# **Hướng Dẫn Cài Đặt ROS Noetic – ROS Tutorial 1 (ROS1)**  

📌 **Thời lượng video**: 11 phút  
📌 **Dành cho**: Người mới bắt đầu với ROS  
📌 **Ngày phát hành video**: 10/11/2020  

## **1️⃣ Giới thiệu về ROS Noetic**  
ROS (**Robot Operating System**) là một framework mã nguồn mở phổ biến dành cho lập trình robot.  

🔥 **ROS Noetic Ninjemys** là phiên bản **cuối cùng** của ROS1, được thiết kế để hỗ trợ **Ubuntu 20.04 (Focal Fossa)** và mang lại tính ổn định lâu dài.  

---

## **2️⃣ Yêu cầu hệ thống**  
✔ **Hệ điều hành**: Ubuntu 20.04 (Desktop hoặc Server)  
✔ **Quyền truy cập**: Terminal với quyền `sudo`  
✔ **Kết nối Internet**: Để tải và cài đặt các gói ROS  

---

## **3️⃣ Hướng dẫn cài đặt từng bước**  

### **🔹 Bước 1: Cấu hình nguồn phần mềm (Software Sources)**  
Thêm kho lưu trữ ROS vào danh sách nguồn của Ubuntu:  
```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
📌 **Giải thích**:  
- Lệnh trên thêm kho lưu trữ chính thức của ROS vào hệ thống.  
- `$(lsb_release -sc)` sẽ tự động lấy tên mã của phiên bản Ubuntu (ở đây là **"focal"**).  

---

### **🔹 Bước 2: Thêm khóa bảo mật GPG**  
Khóa này giúp xác thực các gói ROS trước khi cài đặt:  
```bash
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
🔍 **Lưu ý**: Nếu gặp lỗi khi tải khóa, hãy thử phương pháp thay thế sau:  
```bash
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -
```

---

### **🔹 Bước 3: Cập nhật danh sách gói cài đặt**  
Sau khi thêm nguồn và khóa, chạy lệnh:  
```bash
sudo apt update
```
📌 **Giải thích**: Lệnh này sẽ làm mới danh sách các gói có sẵn trong hệ thống.  

---

### **🔹 Bước 4: Cài đặt ROS Noetic Desktop Full**  
Cài đặt phiên bản đầy đủ của ROS Noetic:  
```bash
sudo apt install ros-noetic-desktop-full
```
🚀 **Gói này bao gồm**:  
✔ **ROS Core** (hệ thống lõi)  
✔ **RViz** (công cụ trực quan hóa)  
✔ **rqt** (bộ công cụ giao diện đồ họa)  
✔ **Các thư viện và công cụ quan trọng khác**  

⏳ **Lưu ý**: Quá trình cài đặt có thể mất vài phút tùy vào tốc độ mạng.  

---

### **🔹 Bước 5: Thiết lập môi trường ROS**  
Để ROS tự động khởi động mỗi lần mở terminal, thêm lệnh sau vào `.bashrc`:  
```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```
Sau đó, áp dụng thay đổi ngay bằng cách chạy:  
```bash
source ~/.bashrc
```

---

### **🔹 Bước 6: Cài đặt các công cụ hỗ trợ phát triển**  
Chạy lệnh sau để cài đặt các công cụ hữu ích:  
```bash
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
**Khởi tạo `rosdep`** (công cụ quản lý phụ thuộc):  
```bash
sudo rosdep init
rosdep update
```

---

## **4️⃣ Kiểm tra cài đặt ROS Noetic**  
### **✅ Kiểm tra ROS đã cài đặt thành công**  
Chạy lệnh:  
```bash
roscore
```
📌 Nếu ROS được cài đặt đúng, bạn sẽ thấy thông báo ROS Master đang chạy.  

⏹ **Để thoát**, nhấn `Ctrl + C`.  

---

## 🎯 **Tóm tắt quy trình cài đặt**  
1️⃣ Thêm nguồn phần mềm của ROS  
2️⃣ Thêm khóa bảo mật GPG  
3️⃣ Cập nhật danh sách gói  
4️⃣ Cài đặt **ROS Noetic Desktop Full**  
5️⃣ Thiết lập biến môi trường  
6️⃣ Cài đặt các công cụ bổ trợ  
7️⃣ Kiểm tra bằng `roscore`  

🔥 **Chúc bạn thành công! 🚀**