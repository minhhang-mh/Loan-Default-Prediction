# Loan-Default-Prediction (Dự báo khả năng vỡ nợ của khách hàng)
## Language: [English](#-english) | [Tiếng Việt](#-tiếng-việt)
---
## 🇬🇧 English
### 1. Project Overview
This project uses Machine Learning to analyze credit history and predict whether a borrower will default on a loan (`Default`). The goal is to help banks detect bad debt early and make better lending decisions.
### 2. Tools & Technologies
- **Language & Environment:** Python, Google Colab
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `seaborn`, `xgboost`, `shap`
### 3. Dataset Summary
- **Dataset:** `Loan_default.csv` with 255,347 rows and 18 columns (no missing values or duplicates).
- **Target Variable (`Default`):**
  - **Class 0 (Non-default):** 225,694 samples (88.39%)
  - **Class 1 (Default):** 29,653 samples (11.61%)
  - *Note:* The data has a severe class imbalance.
### 4. Data Preprocessing
- Removed the identifier column: `LoanID` (reduced to 17 columns).
- Applied One-Hot Encoding (`drop_first=True`) to 7 categorical features (expanded from 17 to 25 columns).
- Split the dataset into Train/Test sets at an 80:20 ratio using stratified sampling (`stratify=y`, Test set: 51,070 samples).
- Scaled numerical features using `StandardScaler` (fitted only on the training set).
- Handled class imbalance using class weights (`compute_class_weight('balanced')`).
### 5. Model Evaluation & Selection
Evaluated on 51,070 test samples:

![model evaluation](<notebook/model evaluation.png>)

- **Selected Model:** **Logistic Regression**
- **Why this model:** While other models had similar overall performance (`ROC-AUC = 0.75`), Logistic Regression achieved the **highest Recall (0.70)**. In loan default prediction, high recall is crucial because it catches the most risky borrowers and minimizes financial loss for the bank.
### 6. Model Interpretation (SHAP)

![SHAP](<notebook/SHAP.png>)

- **Top Factors:** `Age` and `InterestRate` have the strongest impact on default risk.
- **Key Financial Factors:** `MonthsEmployed`, `Income`, and `LoanAmount` play significant roles.
- **Employment & Co-Signer:** Unemployed borrowers or those without a co-signer (`HasCoSigner = No`) are much more likely to default.
- **Low Impact Factors:** Education level and marital status have very little effect on the predictions.
---
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

![model evaluation](<notebook/model evaluation.png>)
* **Mô hình được chọn:** **Logistic Regression**.
* **Lý do:** Đạt điểm phân tách tương đương (`ROC-AUC = 0.75`) nhưng có **Recall cao nhất (0.70)**, giúp ngân hàng phát hiện được nhiều nợ xấu nhất và hạn chế tối đa tổn thất do bỏ sót khách hàng rủi ro.
### 6. Giải thích mô hình (SHAP)

![SHAP](<notebook/SHAP.png>)
* **Tác động mạnh nhất:** `Age` (Tuổi) và `InterestRate` (Lãi suất).
* **Yếu tố tài chính quan trọng:** `MonthsEmployed` (Số tháng làm việc), `Income` (Thu nhập), `LoanAmount` (Khoản vay).
* **Tình trạng việc làm & bảo lãnh:** Khách hàng thất nghiệp (`Unemployed`) hoặc không có bảo lãnh (`HasCoSigner = No`) có nguy cơ vỡ nợ cao hơn.
* **Học vấn và hôn nhân:** Ảnh hưởng rất thấp đến kết quả dự đoán.
