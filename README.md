# Tuần 05: HỌC MÁY

## 1. Tóm tắt Các Yêu cầu Đã Triển khai

| STT | Bài tập | Kỹ thuật | Phân loại Học | Ghi chú |
| :--- | :--- | :--- | :--- | :--- |
| **I.1** | Cài đặt lại thuật toán K-Means | K-Means Clustering | Học không giám sát | Triển khai đầy đủ các hàm cốt lõi (khởi tạo, gán nhãn, cập nhật tâm). |
| **I.2** | Cài đặt lại thuật toán K-NN | K-Nearest Neighbors | Học có giám sát | Cài đặt thủ công và sử dụng `GridSearchCV` để tìm K tối ưu. |
| **I.3** | Cài đặt ứng dụng demo | K-Means & K-NN | Tổng hợp | Tích hợp hai thuật toán vào một ứng dụng trực quan. |
| **BTVN** | Mô tả và Demo Ứng dụng | K-Means, K-NN, Tổng hợp | Ứng dụng thực tế | Mô tả và cài đặt demo mở rộng các thuật toán đã học. |

---

## 2. Phân tích Kỹ thuật và Cài đặt

### 2.1. Kỹ thuật K-Means Clustering (Học không giám sát)

K-Means là một phương pháp đơn giản nhưng hiệu quả để chia dữ liệu thành K cụm dựa trên đặc trưng.

* **Mục tiêu:** Tìm giá trị cực tiểu của hàm mục tiêu J (tổng bình phương khoảng cách từ mỗi điểm dữ liệu đến tâm cụm gần nhất của nó).
* **Triển khai:**
    * **Khởi tạo:** Hàm `kmeans_init_centers` chọn K tâm cụm ngẫu nhiên từ tập dữ liệu.
    * **Gán nhãn:** Hàm `kmeans_predict_labels` gán nhãn cho mỗi điểm dữ liệu bằng cách tìm tâm cụm gần nhất.
    * **Cập nhật:** Hàm `kmeans_update_centers` tính lại tâm cụm là trung bình cộng của tất cả các điểm được gán vào cụm đó.
    * **Trực quan hóa:** Sử dụng thư viện `matplotlib` để vẽ các điểm dữ liệu và tâm cụm qua từng bước lặp, minh họa quá trình hội tụ.

### 2.2. Kỹ thuật K-Nearest Neighbors (K-NN) (Học có giám sát)

K-NN dùng để phân loại quan sát mới bằng cách so sánh điểm tương đồng với dữ liệu đã có nhãn.

* **Nguyên lý Phân loại:** Chọn $K$ điểm láng giềng gần nhất, sau đó gán nhãn cho điểm mới bằng nhãn có số lượng lớn nhất trong $K$ láng giềng đó (ví dụ: $K=5$, 3 tam giác, 2 chữ thập -> gán nhãn tam giác).
* **Cài đặt Hàm `KNN` thủ công:**
    * Tính khoảng cách Euclidean từ mỗi điểm kiểm tra đến tất cả điểm huấn luyện.
    * Sắp xếp khoảng cách theo chiều tăng dần.
    * Đếm số lượng của mỗi lớp trong top K láng giềng để đưa ra quyết định phân loại.
* **Tìm K Tối ưu (Bài 2):**
    * **Phương pháp 1 (Nhìn hình):** Huấn luyện và đánh giá trực quan với $K=1$ và $K=5$ để so sánh kết quả.
    * **Phương pháp 2 (Tự động):** Sử dụng `GridSearchCV` của thư viện `scikit-learn` kết hợp với Cross-Validation (cv=5) để tự động kiểm tra nhiều giá trị $K$ (từ 1 đến 10) và tìm ra giá trị $K$ mang lại độ chính xác cao nhất.

---

## 3. Bài tập Ứng dụng Demo (Bài 4 & 5)

Các bài tập này yêu cầu mô tả và cài đặt demo ứng dụng thực tế cho các thuật toán đã học:

### 3.1. Ứng dụng Demo K-Means và K-NN (Bài 4)

* **K-Means:** * **Mô tả:** Phân khúc khách hàng (Customer Segmentation) dựa trên các đặc trưng như tuổi, thu nhập và tần suất mua hàng.
    * **Demo:** Cài đặt demo K-Means để phân chia dữ liệu khách hàng thành các nhóm mục tiêu khác nhau.
* **K-NN:** * **Mô tả:** Phân loại bệnh tật (Disease Classification) hoặc Phân loại ảnh (Image Classification) dựa trên các điểm đặc trưng.
    * **Demo:** Cài đặt demo K-NN để phân loại một điểm dữ liệu mới vào một trong các lớp đã huấn luyện.

### 3.2. Ứng dụng Tổng hợp (Bài 5)

Bài 5 yêu cầu tổng hợp và mô tả ứng dụng của tất cả các thuật toán đã học (Minimax, Alpha-Beta, TSP, Genetic Algorithm, K-Means, K-NN). Ví dụ:

* **Genetic Algorithm (GA):** Ứng dụng vào Tối ưu hóa thiết kế (ví dụ: tìm hình dạng cánh máy bay tối ưu) hoặc Sắp xếp lịch học phức tạp.
* **TSP:** Ứng dụng vào Tối ưu hóa chuỗi cung ứng và định tuyến xe giao hàng.
* **Minimax/Alpha-Beta:** Ứng dụng vào các game chiến thuật hoặc mô hình hóa các quyết định trong giao dịch tài chính.

---

## 4. Kết luận

Tuần 05 đã hoàn thành việc nắm vững các kỹ thuật học máy cơ bản, cung cấp nền tảng vững chắc để phân loại dữ liệu (K-NN) và phân tích cấu trúc dữ liệu không giám sát (K-Means), đồng thời mở rộng khả năng ứng dụng tổng hợp các thuật toán AI đã học.
