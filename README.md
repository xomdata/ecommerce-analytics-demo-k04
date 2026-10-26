# 📊 Deep-Dive E-commerce Data Analytics: TeddyWorld Case Study

> **Confidential Data Strategy Report** · Hanoi 2026

Dự án phân tích dữ liệu thương mại điện tử, bóc tách **472k phiên truy cập** và **40k bản ghi giỏ hàng** nhằm tìm ra các "nút thắt cổ chai" trong **Vận hành**, **Trải nghiệm UX** và **Chiến lược Bán chéo (Cross-selling)**, từ đó đề xuất kế hoạch hành động cho các bên liên quan (Stakeholders).

---

## Mục lục

- [Mục tiêu](#mục-tiêu)
- [Nguồn dữ liệu](#nguồn-dữ-liệu)
- [Tổng quan chỉ số kinh doanh](#tổng-quan-chỉ-số-kinh-doanh)
- [Phát hiện chính](#phát-hiện-chính)
- [Khuyến nghị & Kế hoạch thực thi](#khuyến-nghị--kế-hoạch-thực-thi)
- [Phương pháp & Công thức](#phương-pháp--công-thức)
- [Cấu trúc báo cáo](#cấu-trúc-báo-cáo)
- [Hạn chế & Lưu ý](#hạn-chế--lưu-ý)
- [Hướng phát triển](#hướng-phát-triển)

---

## Mục tiêu

1. Làm rõ khoảng cách giữa **doanh thu gộp** và **lợi nhuận ròng thực tế** sau chi phí (COGS) và hoàn trả (Refunds).
2. Đánh giá hiệu suất **traffic và tỷ lệ chuyển đổi (CR)** theo nguồn truy cập và thiết bị.
3. Xác định các điểm rơi rớt (drop-off) trong **phễu mua hàng** (Purchasing Funnel).
4. Khai thác **dữ liệu giỏ hàng** để tìm cơ hội Bundle / Cross-sell / Up-sell nhằm tăng AOV.
5. Chuyển hóa insight thành **task list** cụ thể cho từng team.

## Nguồn dữ liệu

| Nguồn | Mô tả |
|---|---|
| Tracking phiên truy cập (Web/App) | Dữ liệu session, nguồn UTM, thiết bị, các bước trong phễu |
| CRM | Thông tin khách hàng và đơn hàng |
| Logistics (Kho vận) | Dữ liệu giao dịch, đảm bảo nhất quán từ *Click → Delivery* |

| Chỉ số chất lượng dữ liệu | Giá trị |
|---|---|
| Tổng phiên phân tích | 472,871 sessions |
| Bản ghi giỏ hàng | 40,000+ |
| Độ tin cậy (dữ liệu đã làm sạch) | 98.5% |

**Thách thức hiện tại:** dữ liệu Marketing và Tài chính còn độ trễ phân mảnh khoảng **2–4 giờ**; cần tối ưu pipeline để phục vụ phân tích thời gian thực (real-time).

## Tổng quan chỉ số kinh doanh

| Chỉ số | Giá trị |
|---|---|
| Sessions | 472,871 |
| Orders | 32,313 |
| Conversion Rate (CR) | 6.83% |
| AOV | $59.99 |
| Revenue | $1,938,510 |
| Refunds | -$85,339 |
| Net Profit | $1,130,801 |
| Net Margin | 58.33% |

## Phát hiện chính

### 1. Sự đánh lừa của doanh thu

- Doanh thu gộp (~$1.93M) là một *vanity metric*; cần nhìn vào Net Margin sau hoàn trả.
- **Mr. Fuzzy** là sản phẩm lõi, chiếm **62.5%** doanh thu (~$1.2M) nhưng có Net Margin thấp nhất (**55.91%**) do COGS và tỷ lệ hoàn tiền cao (5.1%, tương đương 1,237 đơn).
- **Hudson River Mini Bear** là sản phẩm mới có Net Margin cao nhất (**~67%**).

| Sản phẩm | Tỷ trọng doanh thu | Net Margin |
|---|---|---|
| The Original Mr. Fuzzy | 62.5% (~$1.2M) | 55.91% |
| The Forever Love Bear | 17.9% (~$347.7K) | 60.28% |
| The Birthday Sugar Panda | 11.8% (~$229.3K) | 62.46% |
| The Hudson River Mini Bear | 7.8% (~$150.5K) | 67.08% |

- **Tính mùa vụ:** doanh thu đạt đỉnh ở Tháng 11–12, chạm đáy Tháng 3; Forever Love Bear tăng vọt gấp 2–3 lần vào Tháng 2 (Valentine).
- **Mở rộng danh mục:** sản phẩm mới không gây hiện tượng "tự ăn lạm" (cannibalization) lên sản phẩm lõi.

### 2. Hiệu suất traffic & chuyển đổi

- **Nguồn traffic:** G-search 66.8% · Organic 17.6% · B-search 13.3% · Socialbook 2.3% → phụ thuộc lớn vào Google (trả phí/SEO).
- **Thiết bị:** Desktop 69.2% · Mobile 30.8%.
- **CR theo nguồn & thiết bị:**

| Nguồn | Desktop | Mobile |
|---|---|---|
| B-search | 7.85% | 3.01% |
| G-search | 8.43% | 3.17% |
| Organic | **9.89%** | 3.20% |
| Socialbook | 4.99% | 0.83% |

- **Phễu mua hàng (CR so với bước trước):**

| Bước | Desktop | Mobile |
|---|---|---|
| Landed | 327.0k | 145.8k |
| Product | 192.3k (58.8%) | 68.9k (47.2%) |
| Cart | 75.2k (39.1%) | 19.8k (28.7%) |
| Shipping | 52.7k (70.1%) | 11.8k (59.6%) |
| Billing | 43.7k (83.0%) | 8.3k (70.7%) |
| Thank you | 27.8k (63.6%) | 4.5k (54.1%) |
| **CR tổng thể** | **8.5%** | **3.1%** (~2.7 lần thấp hơn) |

- **Khủng hoảng UX Mobile:** rơi rớt 36.4% tại Cart, 45.9% tại Billing; drop-off Product → Cart trên Mobile cao hơn Desktop 7–10%, và chênh lệch ở Billing → Order lên đến ~14% (năm 2015).

### 3. Nút thắt tăng trưởng: Bán chéo & AOV

| Phân loại | Số đơn | Revenue | AOV |
|---|---|---|---|
| Single | 24.6K (76.1%) | 1.3M | $50.8 |
| Cross-sell | 7.7K (23.9%) | 688.3K | $89.3 |

- AOV đơn Cross-sell cao hơn đơn lẻ khoảng **76%**.
- Combo gợi ý dựa trên phân tích giỏ hàng (market basket):

| Combo | Lift | Confidence | Orders |
|---|---|---|---|
| Birthday Sugar Panda + Hudson River Mini Bear | 0.85 | 13.2% | 662 |
| Original Mr. Fuzzy + Hudson River Mini Bear | 0.83 | 12.9% | 3,142 |
| Forever Love Bear + Hudson River Mini Bear | 0.75 | 11.7% | 680 |

## Khuyến nghị & Kế hoạch thực thi

| # | Hạng mục | Nội dung | Team phụ trách |
|---|---|---|---|
| 1 | **Tái thiết kế Mobile UX** | Tối ưu giao diện Mobile tại trang `/billing`; tích hợp Apple Pay / Google Pay để giảm ma sát thanh toán; đưa nút thanh toán lên vị trí dễ thấy (tránh *below the fold*). | Product Team |
| 2 | **Triển khai Bundle / Upsell** | Gợi ý tự động: khi mua Mr. Fuzzy, popup giảm giá 5–10% cho Hudson Mini Bear; ưu tiên sản phẩm biên lợi nhuận cao; dùng combo Confidence cao làm gợi ý mặc định tại Cart. | Marketing & Dev |
| 3 | **Cắt giảm CAC Mobile** | Giảm 50% ngân sách thầu từ khóa *Nonbrand* trên Mobile; dồn ngân sách bảo vệ vị trí Top 1 Desktop Search. | Performance Media |

## Phương pháp & Công thức

```
Net Margin (%) = (Revenue − COGS − Refunds) / Revenue × 100
CR (%)         = Orders / Sessions × 100
AOV            = Revenue / Orders
Drop-off (%)   = 100 − CR giữa hai bước liên tiếp của phễu
```

Các chỉ số khác: **Lift**, **Confidence** (phân tích luật kết hợp / market basket), **Unit Economics**, **Funnel Analysis**.

## Cấu trúc báo cáo

| Phần | Nội dung |
|---|---|
| Mở đầu | Thực trạng nguồn dữ liệu · Tổng quan tình hình kinh doanh |
| **Phần 1** | Sự đánh lừa của doanh thu: Margin Gap, doanh thu & lợi nhuận theo sản phẩm |
| **Phần 2** | Hiệu suất traffic & chuyển đổi: nguồn/thiết bị, phễu, xu hướng drop-off, khủng hoảng UX Mobile |
| **Phần 3** | Nút thắt tăng trưởng: AOV, combo "vàng" từ phân tích giỏ hàng |
| Kết | Chiến lược & kế hoạch thực thi, chuyển giao task cho stakeholders |

## Hạn chế & Lưu ý

- Một số con số trong báo cáo gốc chưa hoàn toàn khớp giữa biểu đồ và phần diễn giải (ví dụ: Net Margin của Hudson River Mini Bear là 67.08% ở biểu đồ nhưng 67.28% ở phần mô tả; tỷ trọng đơn Single là 76.1% và 76.2%; tỷ trọng doanh thu Cross-sell ghi 34.6% trong khi 688.3K / $1.94M ≈ 35.5%). Nên rà soát lại trước khi công bố.
- Các giá trị **Lift < 1** (0.75–0.85) về mặt thống kê cho thấy hai sản phẩm được mua cùng nhau *ít hơn* mức kỳ vọng ngẫu nhiên, nên cách diễn giải "tương hỗ cực mạnh" cần được kiểm chứng lại.
- Biểu đồ xu hướng trong báo cáo bao phủ giai đoạn khoảng **2012–2015**, trong khi báo cáo được lập năm **2026**; cần làm rõ phạm vi thời gian của dữ liệu khi sử dụng.
- Độ trễ 2–4 giờ giữa dữ liệu Marketing và Tài chính có thể ảnh hưởng đến các phân tích gần thời gian thực.

## Hướng phát triển

- [ ] Xây dựng pipeline dữ liệu real-time hợp nhất Marketing – Finance.
- [ ] A/B test giao diện thanh toán Mobile (ví điện tử, vị trí nút thanh toán).
- [ ] A/B test cơ chế Bundle/Upsell và đo lường tác động lên AOV, Net Margin.
- [ ] Theo dõi tỷ lệ hoàn tiền của Mr. Fuzzy và tìm nguyên nhân gốc (chất lượng, mô tả sản phẩm, vận chuyển).
- [ ] Dashboard theo dõi liên tục: CR theo thiết bị, drop-off theo bước, Net Margin theo sản phẩm.

---

*Báo cáo chiến lược dữ liệu 2026 · Bảo mật lưu hành nội bộ*
