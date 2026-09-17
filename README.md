# Supermarket Sales Dashboard

## 1. Tổng quan và bài toán kinh doanh

Dự án sử dụng Excel để phân tích doanh thu bán hàng của chuỗi siêu thị, xây dựng dashboard tương tác theo chi nhánh và tháng.

**Bài toán kinh doanh:** Xác định ngành hàng, nhóm khách hàng và thời điểm đóng góp doanh thu lớn, từ đó đề xuất ưu tiên bán hàng và phân bổ nguồn lực vận hành.

Phân tích tập trung trả lời ba câu hỏi:

- Ngành hàng nào đóng góp nhiều doanh thu nhất?
- Khách hàng Member và Normal khác nhau thế nào về mức đóng góp doanh thu?
- Doanh thu tập trung vào những thứ và khung giờ nào?

Chi nhánh và tháng được dùng để kiểm tra những kết quả này trong từng phạm vi cụ thể.

## 2. Dữ liệu và chuẩn bị dữ liệu

- **Nguồn:** [Supermarket Sales trên Kaggle](https://www.kaggle.com/datasets/faresashraf1001/supermarket-sales/data).
- **Quy mô dữ liệu gốc:** 1.000 dòng, 17 cột.
- **File nguồn:** `SuperMarket Analysis.csv`.
- **Workbook thực hiện:** `SuperMarket Analysis.xlsx`.
- **Phạm vi kết quả:** Toàn bộ 1.000 giao dịch.

Quy trình thực hiện:

**Dữ liệu gốc → Power Query → Dữ liệu phân tích → PivotTable → Dashboard.**

Các bước làm sạch đã thực hiện của dự án:

- Áp dụng TRIM và CLEAN cho các cột văn bản.
- Kiểm tra các cột: 0% lỗi và 0% trống.
- Kiểm tra Unit price, Quantity, Tax, cogs, Sales và Rating lớn hơn 0.
- Kiểm tra trùng Invoice ID, trùng toàn bộ dòng và trùng 14 cột ngoài Invoice ID: không phát hiện trùng.
- Kiểm tra các giá trị distinct
- Đối chiếu trước và sau làm sạch: dữ liệu không thay đổi.

Bổ sung các cột `Revenue`, `Month`, `Weekday_No`, `Weekday` và `Hour` để phục vụ phân tích. 

**Quy ước KPI:** Doanh thu trước thuế = tổng `Sales − Tax 5%`; số giao dịch = đếm `Invoice ID`; số sản phẩm bán = tổng `Quantity`; AOV = doanh thu / số giao dịch; Rating trung bình = trung bình `Rating`.

## 3. Kết quả phân tích và đề xuất

Trong toàn bộ dữ liệu, doanh thu trước thuế đạt **307.587,38**, với **1.000 giao dịch** và **5.510 sản phẩm bán**. Giá trị trung bình mỗi giao dịch đạt **307,59**, Rating trung bình đạt **6,97/10**.

Dashboard thể hiện doanh thu theo ngành hàng, loại khách hàng, thứ trong tuần và giờ. Sử dụng slicer **Branch** và **Month** để chọn phạm vi; bỏ lọc để xem toàn bộ dữ liệu. Các số liệu dưới đây được tính từ sheet `Data_analysis`, không lấy từ trạng thái Pivot đang lọc.

| Chủ đề | Kết quả phân tích | Đề xuất |
|---|---|---|
| **Ngành hàng** | **Food and beverages** dẫn đầu với **53.471,28**, chiếm **17,38%** doanh thu, chỉ cao hơn nhóm đứng thứ hai **Sports and travel** khoảng **973,35**. Tỷ trọng sáu ngành hàng nằm trong khoảng **15,23–17,38%**, cho thấy doanh thu tương đối đồng đều. | Duy trì khả năng đáp ứng ở cả sáu ngành hàng. Chưa có cơ sở để tập trung mạnh vào riêng nhóm dẫn đầu; theo dõi thêm số sản phẩm bán và tồn kho trước khi điều chỉnh phân bổ hàng. |
| **Khách hàng** | **Member đóng góp 58,74%**, Normal đóng góp **41,26%** doanh thu. Member có cả số giao dịch cao hơn (**565 so với 435**) và AOV cao hơn (**319,76 so với 291,78**, khoảng **9,59%**). Chênh lệch doanh thu gắn với cả số lượt mua và giá trị mỗi lượt mua. | Cân nhắc thử ưu đãi theo ngưỡng hóa đơn cho nhóm Normal để nâng AOV. Theo dõi AOV và số giao dịch trong thử nghiệm; kết quả hiện tại chưa chứng minh việc trở thành Member làm khách hàng chi tiêu nhiều hơn. |
| **Thời điểm** | **19:00–19:59** dẫn đầu cả doanh thu (**37.809,06**, khoảng **12,29%**) và số giao dịch (**113**, chiếm **11,3%**). Tuy nhiên, giờ có nhiều giao dịch nhất khác nhau theo chi nhánh: **Alex là 10 giờ, Cairo là 19 giờ, Giza là 10 giờ**. | Cân nhắc chuẩn bị hàng và bố trí nhân sự trước giờ nhiều giao dịch của từng chi nhánh, thay vì áp dụng chung khung 19 giờ cho toàn chuỗi. Theo dõi số giao dịch và doanh thu theo giờ để đánh giá điều chỉnh. |


## 4. Giới hạn

Dự án sử dụng dữ liệu nhân tạo để rèn luyện kỹ năng Excel, Power Query và PivotTable. Các insight và đề xuất minh họa cách suy luận từ dữ liệu, chưa mang nhiều ý nghĩa thực tế.


