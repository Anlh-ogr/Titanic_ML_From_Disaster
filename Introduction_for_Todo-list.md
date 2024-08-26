# Project Board - Titanic Machine Learning

## 1. Data Collection

- Sử dụng dữ liệu có sẵn "https://github.com/Anlh-ogr/Titanic_ML_From_Disaster/tree/main/Titanic_Project_Information_Data"

## 2. Data Preprocessing

- Xử lý các giá trị bị thiếu, chuẩn hóa dữ liệu, chuyển đổi các biến phân loại, và phân chia tập dữ liệu.

## 3. Exploratory Data Analysis (EDA)

- Phân tích dữ liệu để hiểu rõ hơn về các mối quan hệ giữa các biến, đặc biệt là các yếu tố ảnh hưởng đến sự sống sót.

## 4. Model Selection

### **YOLOv5**

- **Mục đích:** Nhận diện đối tượng trong ảnh.
- **Không phù hợp:** YOLOv5 không phù hợp cho bài toán phân loại như dự đoán sự sống sót của hành khách vì nó chủ yếu dùng cho các bài toán nhận diện đối tượng trong ảnh.

### **Hồi Quy Tuyến Tính (Linear Regression)**

- **Mục đích:** Dự đoán giá trị liên tục.
- **Không phù hợp:** Hồi quy tuyến tính không phải là lựa chọn tốt cho bài toán phân loại nhị phân như dự đoán sự sống sót. Hồi quy logistic là lựa chọn tốt hơn.

### **Scikit-Learn**

- **Mục đích:** Thư viện máy học trong Python cho các mô hình phân loại, hồi quy, và clustering.
- **Phù hợp:** Sử dụng Scikit-Learn để triển khai các mô hình phân loại cho bài toán dự đoán sống sót, bao gồm:
  - **Logistic Regression:** Mô hình phân loại cơ bản, hiệu quả cho bài toán phân loại nhị phân.
  - **Decision Tree Classifier:** Mô hình phân loại dựa trên cấu trúc cây quyết định, dễ giải thích.
  - **Random Forest Classifier:** Mô hình ensemble kết hợp nhiều cây quyết định để cải thiện độ chính xác và giảm overfitting.
  - **Gradient Boosting Classifier:** Mô hình ensemble nâng cao, hiệu quả trong việc tối ưu hóa hiệu suất phân loại với các tham số điều chỉnh.

### **TensorFlow Lite**

- **Mục đích:** Triển khai mô hình TensorFlow trên thiết bị di động và nhúng.
- **Phù hợp:** Nếu bạn muốn triển khai mô hình phân loại đã huấn luyện trên môi trường di động, TensorFlow Lite là lựa chọn tốt. Tuy nhiên, trước tiên, cần huấn luyện mô hình trên TensorFlow rồi chuyển đổi sang TensorFlow Lite.

### **Llama 3**

- **Mục đích:** Mô hình sinh văn bản.
- **Không phù hợp:** Llama 3 không phù hợp cho bài toán phân loại dữ liệu kiểu bảng như Titanic.

### **Gemma**

- **Mục đích:** Mô hình sinh văn bản sử dụng Keras.
- **Không phù hợp:** Gemma không phù hợp cho bài toán phân loại kiểu bảng như Titanic.

## 5. Model Training

### Mô Hình Được Chọn

- **Scikit-Learn** sẽ được sử dụng để triển khai các mô hình phân loại cho bài toán dự đoán sự sống sót của hành khách.

### Các Mô Hình Cụ Thể

- **Logistic Regression**

  - **Mô tả:** Mô hình phân loại cơ bản để dự đoán xác suất sự sống sót.
  - **Lý do chọn:** Đơn giản, dễ hiểu, và hiệu quả cho bài toán phân loại nhị phân.
- **Decision Tree Classifier**

  - **Mô tả:** Mô hình phân loại sử dụng cấu trúc cây quyết định để phân loại dữ liệu.
  - **Lý do chọn:** Cung cấp sự giải thích dễ dàng về các quyết định phân loại.
- **Random Forest Classifier**

  - **Mô tả:** Mô hình ensemble kết hợp nhiều cây quyết định để cải thiện hiệu suất.
  - **Lý do chọn:** Giúp giảm overfitting và cải thiện độ chính xác tổng thể.
- **Gradient Boosting Classifier**

  - **Mô tả:** Mô hình ensemble nâng cao để tăng cường hiệu suất phân loại.
  - **Lý do chọn:** Hiệu quả trong việc tối ưu hóa hiệu suất phân loại với các tham số điều chỉnh.

## 6. Model Evaluation

- Đánh giá mô hình trên tập dữ liệu kiểm tra, sử dụng các chỉ số như AUC-ROC, accuracy, precision, và recall.

## 7. Hyperparameter Tuning

- Tối ưu hóa các tham số của mô hình để cải thiện độ chính xác và hiệu quả.

## 8. Final Model Deployment

- Đưa mô hình lên sản phẩm (ví dụ: lưu mô hình dưới dạng pickle hoặc triển khai với TensorFlow Lite).

## 9. Documentation

- Viết tài liệu chi tiết về cách thực hiện, kết quả, và hướng dẫn triển khai.
