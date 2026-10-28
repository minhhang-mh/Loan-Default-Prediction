# Loan-Default-Prediction (Dự báo khả năng vỡ nợ của khách hàng)
## Language: [English](#-english) | [Tiếng Việt](#-tiếng-việt)
---
## 🇬🇧 English
### 1. 
## 🇻🇳 Tiếng Việt
### 1. Tổng quan dự án
Dự án áp dụng Machine Learning để phân tích lịch sử tín dụng và dự đoán nguy cơ khách hàng vỡ nợ (`Default`), giúp ngân hàng giảm thiểu nợ xấu và tối ưu phê duyệt tín dụng.
### 2. Công cụ
* **Ngôn ngữ & Môi trường:** Python, Google Colab
* **Thư viện:** `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `seaborn`, `xgboost`, `shap`
### 3. Tóm tắt bộ dữ liệu
* **Tập dữ liệu:** `Loan_default.csv` gồm 255.347 dòng và 18 cột; không có giá trị khuyết hay trùng lặp.
* **Biến mục tiêu (`Default`):**
  * Nhãn 0 (Không vỡ nợ): 225.694 mẫu (88,39%).
  * Nhãn 1 (Vỡ nợ): 29.653 mẫu (11,61%).
  * *Đặc điểm:* Dữ liệu mất cân bằng lớp nghiêm trọng.
### 4. Xử lý dữ liệu
* Xóa cột định danh không cần thiết: `LoanID` (giảm xuống 17 cột).
* Mã hóa One-Hot (`drop_first=True`) 7 biến phân loại (tăng từ 17 lên 25 cột).
* Chia tập Train/Test theo tỷ lệ 80:20 (phân tầng `stratify=y`, tập Test: 51.070 mẫu).
* Chuẩn hóa biến số định lượng bằng `StandardScaler` (chỉ fit trên tập Train).
* Xử lý mất cân bằng lớp bằng trọng số `compute_class_weight('balanced')`.
### 5. Kết quả mô hình
Đánh giá trên 51.070 mẫu tập Test:
![
