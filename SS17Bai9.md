## Bài 9: Thiết Kế Không Gian Đa Profile Và Kiến Trúc Bookmark Cho Trạm Khám Bệnh

# 1: Vấn đề 

- Tại trạm y tế, mỗi phòng khám chỉ được trang bị 01 bộ máy tính để bàn

- Hậu quả là phòng khám liên tục gặp sự cố hỗn loạn

# 2: Yêu cầu 

**Phần 1: Báo cáo phân tích kiến trúc đa Profile**

**1.** Phân tích nguyên nhân sâu xa dẫn đến hiện tượng 'văng phiên đăng nhập' (Session Conflict) dưới góc độ lưu trữ Cookies trong thư mục User Data khi dùng chung 1 Profile.

**2.** Thiết kế Mô hình 3 Profile chuyên dụng cho máy tính trạm khám CarePulse. Với mỗi Profile, nêu rõ: Tên Profile, Mục đích sử dụng, Màu Theme nhận diện thị giác, và các loại dữ liệu được lưu trữ độc lập (Cookies, History, Bookmarks, Extensions).

**Phần 2: Thiết kế hệ thống Bookmark & Quy trình an toàn**

**3** Dựng cây thư mục Bookmark

**4** Hướng dẫn áp dụng mẹo Favicon-Only cho 4 trang web dùng hàng ngày (CarePulse, Cổng BHYT, Dược thư, Google Dịch) để tiết kiệm diện tích thanh công cụ gấp 3 lần.

**5.** Xử lý Bẫy an ninh: Khi có đoàn thanh tra hoặc khách mượn máy tính kiểm tra trong 30 phút, nhân viên phòng khám phải kích hoạt chế độ duyệt web nào (Guest Profile hay Incognito)? Giải thích lý do và cảnh báo nguy cơ nếu bật tính năng Cloud Sync tài khoản cá nhân trên máy trạm y tế này.

# 3: Cách làm

**Phần 1**

**1** Báo cáo phân tích:
- Nguyên nhân của tình trạng này là do các nhân viên đều sử dụng chung một cửa sổ Chrome và một Profile

- Do dùng chung một Profile nên dữ liệu đăng nhập của mọi người có thể bị ảnh hưởng lẫn nhau.

**2** Mô hình 3 Profile

| Tên Profile | Mục đích sử dụng | Màu nhận diện |
|---|---|---|
| Work | Dành cho bác sĩ và điều dưỡng làm việc trên CarePulse. | Xanh dương |
| Personal | Dành cho nhân viên sử dụng các trang web cá nhân. | Tím |
| Sandbox/Test | Dành cho bác sĩ thực tập học tập và thử nghiệm. | Cam |

**Phần 2**

**3** Cây thư mục Bookmark

    01_CarePulse_Clinic
        - CarePulse
        - Cổng BHYT
        - Hồ sơ bệnh nhân
        - Lịch khám bệnh

    02_Pharma_Portal
        - Dược thư Quốc gia
        - Cổng thông tin Bộ Y tế
        - Tra cứu thuốc
        - Tra cứu tương tác thuốc

    03_Medical_Tools
        - Google Dịch
        - Công cụ tính BMI
        - Công cụ tính liều thuốc
        - Tra cứu chỉ số xét nghiệm

**4** Cách thực hiện:
1. Nhấn chuột phải vào dấu trang cần chỉnh sửa.
2. Chọn Chỉnh sửa.
3. Xóa tên trang web trong ô Tên.
4. Giữ nguyên địa chỉ trang web.
5. Nhấn Lưu.

**5**

- Khi có đoàn thanh tra hoặc khách mượn máy tính trong khoảng 30 phút, nhân viên nên sử dụng chế độ Guest Profile (Chế độ khách).

- Em chọn chế độ này vì người mượn máy có thể sử dụng trình duyệt mà không cần truy cập vào các dữ liệu cá nhân đã lưu trong Profile chính. Khi đóng cửa sổ Guest, dữ liệu duyệt web của phiên khách sẽ bị xóa.

- Em không chọn Incognito vì chế độ này vẫn nằm trong Profile hiện tại và không tạo một Profile khách riêng biệt.

- Theo em, không nên bật đồng bộ Cloud Sync bằng tài khoản Google cá nhân trên máy tính dùng chung của trạm y tế.

- Vì nếu bật đồng bộ, lịch sử truy cập, dấu trang và mật khẩu có thể được lưu trên tài khoản cá nhân. Khi người khác sử dụng máy tính, thông tin cá nhân có thể bị lộ nếu không đăng xuất đúng cách.