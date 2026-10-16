


# Phần 1 Phân tích 
1.**Xác định Input/Output**

| Loại | Mô tả|
|-|-|
|Input | Cảm biến: độ ẩm đất, nhiệt độ không khí, độ ẩm không khí, mức nước bể  |
|Process|So sánh số liệu thu thập với ngưỡng đã cấu hình|
|Output |Bơm nước tự động bật/tắt. Cảnh báo qua màn hình;điện thoại khi có sự bất thường |

2. **Sơ đồ phối hợp phần cứng của hệ thống trang trại.**

*Cảm biến (độ ẩm, nhiệt độ) => SoC (Bộ vi điều khiển) => Thiết bị thực thi (Bơm nước)*

SoC (Hệ thống trên Chip): Là trung tâm xử lý tích hợp CPU, bộ nhớ, giao tiếp => nhận tín hiệu, thực thi chương trình, ra lệnh điều khiển bơm nước theo quy tắc đã lập trình.
# Phần 2 Triển khai 

 ##**File README.md hoàn chỉnh**
 ### 🚀 Dự án Smart-Farm  Hệ thống Trang Trại Thông Minh 
 > *Giải pháp tự động hóa giám sát và chăm sóc vườn Lan tại Trang trại Lan, tích hợp công nghệ IoT để tối ưu nước tưới, tiết kiệm nhân công và nâng cao chất lượng cây trồng.* --- 
 ####  Mô tả **Smart-Farm** là hệ thống giám sát và điều khiển tự động
  ựa trên nền tảng **SoC** và mô hình **IPO :Input =>Xử lý => Đầu ra**. Hệ thống tự động thu thập số liệu môi trường, phân tích theo quy trình **DIKW** và ra quyết định tưới nước phù hợp, giúp người nông dân quản lý vườn Lan một cách chính xác và hiệu quả. 
 > **Chu kỳ hoạt động của CPU khi nhận lệnh tưới:** 
 > > *"Fetch : Lấy lệnh từ bộ nhớ, đọc giá trị độ ẩm đất hiện tại
 > Decode : Phân tích ý nghĩa lệnh, so sánh với ngưỡng tối thiểu đã đặt; Execute : Thực thi: nếu độ ẩm thấp hơn ngưỡng, gửi tín hiệu bật bơm nước trong khoảng thời gian đã cấu hình, sau đó cập nhật trạng thái vào nhật ký."* 
 -----
 ###  Sơ đồ Hệ thống ![Sơ đồ Smart-Farm](https://rikkeiedu-storage.s3.ap-southeast-2.amazonaws.com/uploads/editor-images/1787648283613_687ec2e7-229c-4942-a347-080fae59560a.webp) *Sơ đồ luồng dữ liệu và phối hợp phần cứng trong hệ thống Smart-Farm* --- 
 ### ⚙️ Hướng dẫn Cài đặt ```bash 
 1. Tải mã nguồn 
git clone https://github.com/smart-farm-lan/smart-farm-system.git cd smart-farm-system 
 2. Cấu hình
- tham số  ``cp config.example.json config.json ``
-  Điền ngưỡng độ ẩm, thời gian tưới, thông số kết nối mạng

 **Tính năng Chính**
- [x] Tự động đo liên tục độ ẩm đất, nhiệt độ, độ ẩm không khí 
- [x] Quyết định tưới nước dựa trên ngưỡng đã cài đặt không cần can thiệp thủ công 
- [x] Ghi nhật ký chi tiết thời gian, số liệu và trạng thái thiết bị 
- [x] Thông báo khi có giá trị bất thường hoặc thiết bị có dấu hiệu lỗi 
- [x] Xem trạng thái hệ thống từ xa qua điện thoại/máy tính 
- [ ] Điều khiển thủ công bật/tắt bơm khi cần can thiệp đặc biệt

# Phần 3 Kiểm thử 
Khi bộ nhớ RAM bị đầy do nhật ký: 
- Hệ thống có cơ chế tự động xóa bản ghi cũ nhất nếu bật chế độ quản lý bộ nhớ tự động trong  Xử lý thủ công an toàn: 
- Tạm dừng hệ thống: Dừng trên giao diện hoặc lệnh ```systemctl stop smart-farm``` 
- Xóa tệp cũ tại thư mục ```logs```
- giữ lại bản ghi 7 ngày gần nhất nếu có thể Không xóa tệp ```config.json``` hoặc thư mục data
-  chứa cấu hình quan trọng 
- **Khởi động lại: python main.py hoặc khởi động lại thiết bị SoC Để phòng ngừa: bật đồng bộ tự động lên đám mây**
=> nhật ký được chuyển đi và giải phóng bộ nhớ nội bộ


