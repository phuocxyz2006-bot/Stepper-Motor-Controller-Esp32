# 🛜 ESP32 Web-based Stepper Motor Controller

Dự án điều khiển động cơ bước (Stepper Motor - thường là 28BYJ-48 qua module ULN2003) thông qua giao diện Web Dashboard được host trực tiếp trên vi điều khiển ESP32 (Chế độ Access Point).

## 🌟 Tính năng nổi bật
* **Web Server Độc Lập:** ESP32 tự phát WiFi (Access Point), không cần phụ thuộc vào mạng router hay internet bên ngoài.
* **Giao diện Dashboard Hiện Đại:** UI/UX được code bằng HTML/CSS/JS với giao diện Responsive, dễ dàng thao tác trên điện thoại.
* **Điều khiển thời gian thực:** 
  - Quay thuận / Quay nghịch tức thì.
  - Dừng khẩn cấp (Emergency Stop).
  - Tiếp tục hành trình dang dở.
  - Thay đổi tốc độ quay trực tiếp bằng vòng/phút (RPM).
* **Thuật toán tối ưu:** 
  - Sử dụng hàm `micros()` để điều khiển động cơ (Non-blocking), giúp Web Server không bị treo khi động cơ đang quay.
  - Tích hợp biến gia tốc (`GIA_TOC`) giúp động cơ tăng/giảm tốc mượt mà, không bị trượt bước.

## 🛠 Sơ đồ kết nối (Pinout)
<img width="3000" height="2517" alt="circuit_image (4)" src="https://github.com/user-attachments/assets/dab1ec8c-7bb0-4b85-a181-a861b9f952ef" />
**Bảng đấu nối ESP32 với Module ULN2003 (Động cơ bước):**

| Chân trên ESP32 | Chân trên ULN2003 | Ghi chú |
| :---: | :---: | :--- |
| **GPIO 12** | IN1 | Tín hiệu pha 1 |
| **GPIO 14** | IN2 | Tín hiệu pha 2 |
| **GPIO 27** | IN3 | Tín hiệu pha 3 |
| **GPIO 26** | IN4 | Tín hiệu pha 4 |
| **VIN / 5V** | VCC | Nguồn cấp cho động cơ |
| **GND** | GND | Nối chung mass |

## 🚀 Hướng dẫn kết nối và sử dụng

1. **Cấp nguồn:** Nạp code vào ESP32 và cấp nguồn.
2. **Kết nối WiFi:** Dùng điện thoại hoặc laptop tìm và kết nối với mạng WiFi do ESP32 phát ra:
   - **Tên WiFi (SSID):** `ESP32_DongCo`
   - **Mật khẩu:** `12345678`
3. **Mở Bảng điều khiển:** 
   - Mở trình duyệt web (Chrome/Safari).
   - Truy cập vào địa chỉ IP: **`192.168.4.1`**
4. **Thao tác:** Bấm các nút trên màn hình để điều khiển chiều quay, hoặc nhập thông số vào ô "Tốc độ (RPM)" rồi bấm "Cài tốc độ".

## 📦 Yêu cầu phần mềm
- **Môi trường:** Arduino IDE hoặc VS Code (PlatformIO).
- **Thư viện:** `WiFi.h` và `WebServer.h` (Thường đã có sẵn trong gói cài đặt ESP32 core).
