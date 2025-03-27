### 🌟 Giới Thiệu về ROS Node và Giao Tiếp Giữa Các Node  

Video hướng dẫn khái niệm **ROS Node**, cách các node giao tiếp với nhau trong hệ thống ROS, và minh họa bằng một ví dụ thực tế đơn giản với hai node: **Talker** và **Listener**.

---

## 🔹 **1. ROS Node là gì?**  
- **Node** trong ROS là một tiến trình (**process**) độc lập đảm nhiệm một chức năng cụ thể.  
- Các node giao tiếp với nhau thông qua **messages** (tin nhắn) bằng cơ chế **Publish/Subscribe** hoặc **Services**.  
- Ví dụ trong một hệ thống robot:
  - **Node A**: Đọc dữ liệu từ cảm biến.  
  - **Node B**: Xử lý dữ liệu và đưa ra quyết định.  
  - **Node C**: Điều khiển động cơ.  
- Việc phân chia thành nhiều node giúp **dễ bảo trì, mở rộng** và tận dụng sức mạnh xử lý đa luồng.

---

## 🔹 **2. Cơ Chế Giao Tiếp Giữa Các Node**  
- **Topic**: Kênh trung gian để các node gửi/nhận tin nhắn.  
- **Publisher**: Node gửi dữ liệu lên một topic.  
- **Subscriber**: Node đăng ký nhận dữ liệu từ topic đó.  
- **ROS Master (roscore)**: Điều phối và quản lý các node trong hệ thống.  

💡 **Minh họa cơ chế giao tiếp:**  
📢 **Talker (Publisher)** ➡ gửi tin nhắn lên **/chatter** ➡ 📩 **Listener (Subscriber)** nhận và hiển thị.

---

## 🔹 **3. Thực Hành: Chạy Talker và Listener**  
### 🛠 **Chuẩn bị môi trường**
1️⃣ Mở terminal và khởi động **ROS Master**:  
   ```bash
   roscore
   ```
   Giữ terminal này chạy để đảm bảo hệ thống hoạt động.

---

### 🚀 **Bước 1: Chạy Node Talker**  
📌 Mở terminal thứ hai và chạy:  
   ```bash
   rosrun rospy_tutorials talker
   ```
   🔹 **Chức năng:** Gửi liên tục tin nhắn `"Hello World"` lên topic `/chatter`.

---

### 🎧 **Bước 2: Chạy Node Listener**  
📌 Mở terminal thứ ba và chạy:  
   ```bash
   rosrun rospy_tutorials listener
   ```
   🔹 **Chức năng:** Nhận tin nhắn từ topic `/chatter` và in ra màn hình.  

📌 **Kết quả mong đợi:**  
- Terminal **Talker** sẽ hiển thị:  
  ```
  [INFO] [time]: Hello World 1
  [INFO] [time]: Hello World 2
  ```
- Terminal **Listener** sẽ hiển thị:  
  ```
  I heard: Hello World 1
  I heard: Hello World 2
  ```

---

## 🔹 **4. Kiểm Tra và Giám Sát Hoạt Động của Node**
- 📡 **Xem danh sách các topic đang hoạt động:**  
   ```bash
   rostopic list
   ```
   ✅ Bạn sẽ thấy `/chatter` xuất hiện.  

- 🧐 **Quan sát dữ liệu trên topic:**  
   ```bash
   rostopic echo /chatter
   ```
   ✅ Hiển thị nội dung tin nhắn `"Hello World"` mà **Talker** gửi đi.

- ⏳ **Dừng chương trình**:  
   Nhấn `Ctrl + C` trong từng terminal để dừng các node.

---

## 🔹 **5. Kết Luận và Ứng Dụng Thực Tế**  
- ROS Node giúp xây dựng hệ thống robot **linh hoạt, mở rộng dễ dàng**.  
- Các thành phần giao tiếp theo mô hình **publish/subscribe**, giúp **đa tiến trình** hoạt động hiệu quả.  
- Bạn có thể tự viết các node tùy chỉnh để **đọc cảm biến, điều khiển robot** hoặc **tạo AI cho ROS**.

🚀 **Thử thách tiếp theo:**  
🔹 Viết một **Node Python** để tự tạo **Publisher/Subscriber**! 🚀