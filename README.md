# 📊 Deep-Dive E-commerce Data Analytics: TeddyWorld Case Study

## 🎯 1. Bối cảnh & Mục tiêu dự án

Dự án thực hiện phân tích chuyên sâu trên tập dữ liệu thương mại điện tử quy mô lớn bao gồm **472,871 phiên truy cập** và hơn **40,000 dữ liệu giỏ hàng**. Thay vì chỉ tập trung vào doanh thu bề nổi, dự án đi sâu vào việc tìm kiếm các "nút thắt cổ chai" trong vận hành và trải nghiệm người dùng.

**Mục tiêu chính:**

* 🔍 **Giải mã hiện tượng trượt lợi nhuận:** Phân tích sự khác biệt giữa doanh thu gộp và lợi nhuận thực tế sau khi trừ chi phí hoàn tiền.
* 📉 **Tối ưu hóa phễu chuyển đổi:** Xác định các điểm nghẽn khiến tỷ lệ chuyển đổi (CR) trên Mobile thấp hơn Desktop.
* 📈 **Tăng trưởng giá trị đơn hàng (AOV):** Sử dụng phân tích giỏ hàng (MBA) để đề xuất các chiến lược bán chéo (Cross-selling) hiệu quả.

## 💻 2. Techstack (Công cụ sử dụng)

Dự án được xây dựng trên nền tảng Python với các thư viện chuyên dụng cho khoa học dữ liệu:

* **Ngôn ngữ:** `Python` 🐍
* **Thư viện xử lý dữ liệu:** `pandas`, `numpy`
* **Trực quan hóa dữ liệu:**
* `matplotlib` & `seaborn`: Biểu đồ tĩnh và phân tích xu hướng.
* `plotly`: Xây dựng phễu chuyển đổi (Funnel) tương tác đa chiều.


* **Công cụ hỗ trợ:** `Excel` (Xử lý thô), `Jupyter Notebook` 📓

## 💡 3. Insight Chiến lược (Key Insights)

### 📉 3.1. Sự đánh lừa của Doanh thu (Margin Gap)

* Doanh thu gộp đạt **$1.93M** là một chỉ số cần được nhìn nhận lại vì thực tế biên lợi nhuận ròng chỉ đạt **58.33%**.
* Sản phẩm chủ lực `The Original Mr. Fuzzy` tạo ra $1.2M doanh thu nhưng có tỷ lệ hoàn tiền cao (5.1%), khiến biên lợi nhuận ròng thấp nhất danh mục (**55.91%**).
* Sản phẩm `The Hudson River Mini bear` có tiềm năng lớn với biên lợi nhuận thực tế đạt **67.08%**.

### 📱 3.2. Hiệu suất Traffic & Điểm nghẽn UX

* **Sự thống trị của Desktop:** Chiếm gần **70%** lượng traffic và có tỷ lệ chuyển đổi cao gấp **~2.7 lần** so với Mobile.
* **Khủng hoảng Mobile UX:**
* Tỷ lệ khách hàng chuyển từ xem sản phẩm sang giỏ hàng trên Mobile chỉ đạt **28.7%** (so với 39.1% trên Desktop).
* **45.9%** khách hàng bỏ cuộc tại bước thanh toán (`/billing`) trên Mobile do lỗi hiển thị và không tương thích.
* Nút "Thanh toán ngay" bị che khuất dưới nếp gấp màn hình trên thiết bị di động.



### 🤝 3.3. Đòn bẩy Bán chéo (Cross-selling)

* Đơn hàng bán chéo có **AOV $89.3**, cao hơn **76%** so với đơn hàng đơn lẻ ($50.8).
* Nhóm Cross-sell đóng góp tới **34.6%** tổng doanh thu dù chỉ chiếm **23.9%** số lượng đơn hàng.

## 🚀 4. Khuyến nghị chiến lược (Recommendations)

### 🛠️ 1. Tái thiết kế Mobile UX (Product Team)

* Tối ưu hóa giao diện trang thanh toán, tích hợp các ví điện tử như **Apple/Google Pay** để giảm ma sát.
* Điều chỉnh thiết kế để nút "Thanh toán" luôn hiển thị ở vị trí thuận lợi, tránh bị che khuất.

### 🎁 2. Triển khai Bundle & Upsell (Marketing & Dev)

* **Combo Sức mạnh (High Lift):** Chạy quảng cáo Bundle cho cặp `The Birthday Sugar Panda` + `The Hudson River Mini bear`.
* **Sản phẩm gợi ý (High Confidence):** Gợi ý mặc định `The Hudson River Mini Bear` khi khách hàng mua `Mr. Fuzzy` tại bước thanh toán.

### 💰 3. Tối ưu hóa ngân sách Marketing (Performance Media)

* **Cắt giảm CAC Mobile:** Giảm 50% thầu từ khóa không thương hiệu (Nonbrand) trên thiết bị di động do hiệu quả chuyển đổi thấp.
* **Bảo vệ Desktop:** Dồn ngân sách để duy trì vị trí Top 1 tìm kiếm trên Desktop nhằm đảm bảo ROI.

---

*Dự án được thực hiện bởi Tu Nguyen - Lead Xóm Data (Hanoi 2026)* 🖋️


