# 🧩 Phân Tích Và Phân Loại Khách Hàng Dựa Trên RFM, K-Means, ANN và Random Forest

## 📘 Giới thiệu

Dự án này tập trung vào việc **khai thác dữ liệu hành vi khách hàng** trong thương mại điện tử bằng các kỹ thuật **Data Mining**, bao gồm:

- **Phân tích RFM (Recency - Frequency - Monetary)** để đánh giá giá trị khách hàng.  
- **Phân cụm K-Means** để nhóm khách hàng theo hành vi.  
- **Huấn luyện mô hình học máy (ANN và Random Forest)** để tự động dự đoán phân khúc khách hàng mới.  

Mục tiêu cuối cùng là giúp doanh nghiệp **hiểu rõ khách hàng hơn**, từ đó **tối ưu chiến lược marketing** và **giữ chân khách hàng hiệu quả**.

---

## 🎯 Mục tiêu chính

- Phân tích dữ liệu giao dịch để tính toán các chỉ số RFM.  
- Phân nhóm khách hàng bằng **K-Means**.  
- Huấn luyện mô hình **ANN** và **Random Forest** dựa trên nhãn từ KMeans.  
- So sánh hiệu năng các mô hình qua **Accuracy, F1-score, Log Loss, ROC-AUC**.  
- Ứng dụng kết quả vào chiến lược **CRM** và **Marketing cá nhân hóa**.

---

## 🧠 Quy trình thực hiện

### 1️⃣ Xử lý dữ liệu
- Làm sạch dữ liệu giao dịch, loại bỏ giá trị thiếu hoặc lỗi.
- Tính toán tổng giá trị giao dịch cho từng khách hàng.

### 2️⃣ Phân tích RFM
- Tính 3 chỉ số:
  - **Recency (R)**: số ngày kể từ lần mua gần nhất.  
  - **Frequency (F)**: số lần mua hàng.  
  - **Monetary (M)**: tổng chi tiêu.  
- Chuẩn hóa dữ liệu bằng `StandardScaler`.

### 3️⃣ Phân cụm K-Means
- Xác định số cụm tối ưu bằng **Elbow Method**.  
- Phân nhóm khách hàng thành 4 cụm:
  1. **Active Loyal** – khách hàng trung thành  
  2. **Potential Loyalists** – khách hàng tiềm năng  
  3. **Big Spenders One-time** – chi tiêu cao nhưng ít mua  
  4. **At-risk / Churned** – có nguy cơ rời bỏ  
- Trực quan hóa bằng **PCA** và biểu đồ phân bố cụm.

### 4️⃣ Huấn luyện mô hình phân loại
- Sử dụng 2 mô hình:
  - **Artificial Neural Network (ANN)**  
  - **Random Forest Classifier**
- Đánh giá bằng Accuracy, Macro-F1, Log Loss, ROC-AUC.
- Giải quyết mất cân bằng lớp bằng `class_weight='balanced'`.

### 5️⃣ Trực quan hóa kết quả
- Biểu đồ doanh thu, phân bố khách hàng, cụm RFM và ma trận nhầm lẫn.

---

## 📊 Kết quả thực nghiệm

| Chỉ số | ANN | Random Forest |
|--------|-----|----------------|
| **Accuracy** | 0.992 – 0.993 | **0.997 (cao hơn)** |
| **Macro-F1** | 0.993 | **0.997** |
| **Log Loss** | **0.056 (thấp hơn)** | 0.057 |
| **ROC-AUC** | ≈ 1.0 | ≈ 1.0 |
| **Thời gian huấn luyện** | ~34.86s | **~0.53s (nhanh hơn ~66 lần)** |

➡️ **Random Forest** có độ chính xác tổng thể cao hơn, đặc biệt ở các lớp hiếm.  
➡️ **ANN** cho dự đoán xác suất “tự tin” hơn và mượt hơn.

---

## 💡 Ý nghĩa kinh doanh

| Phân khúc | Đặc điểm | Hành động gợi ý |
|------------|-----------|-----------------|
| **VIP / Active Loyal** | Mua thường xuyên, chi tiêu cao | Tạo chương trình tích điểm, ưu đãi đặc biệt |
| **Potential Loyalists** | Mua đều, giá trị trung bình | Gửi email khuyến khích mua lại |
| **Big Spenders One-time** | Chi tiêu cao nhưng ít quay lại | Gợi ý sản phẩm tương tự, giảm giá tái mua |
| **At-risk / Churned** | Ít mua gần đây | Gửi ưu đãi tái kích hoạt, chăm sóc đặc biệt |

---

## 🧩 Công nghệ sử dụng

| Thành phần | Công cụ |
|-------------|----------|
| Ngôn ngữ | Python 3.x |
| Xử lý dữ liệu | pandas, numpy |
| Trực quan hóa | matplotlib, seaborn |
| Machine Learning | scikit-learn, tensorflow, keras |
| Công cụ hỗ trợ | Gradio / Streamlit (demo dự đoán) |

---

## ⚙️ Cài đặt và chạy

### 1️⃣ Clone repo
```bash
git clone https://github.com/<tên-người-dùng>/<tên-repo>.git
cd <tên-repo>
