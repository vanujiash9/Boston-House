

# Dự án Phân tích & Dự đoán giá nhà Boston

Dự án này nhằm **phân tích** và **dự đoán giá nhà** (MEDV) dựa trên **Boston Housing dataset**. Qua đó, ta so sánh hiệu năng giữa nhiều mô hình học máy (Linear Regression, Ridge, SVR, Decision Tree, KNN, Gradient Boosting, …) và **đánh giá** mô hình nào phù hợp nhất.

## 1. Giới thiệu

- **Dữ liệu**: [Boston Housing dataset](https://archive.ics.uci.edu/ml/datasets/Housing) (bản gốc).  
- **Mục tiêu**: Dự đoán giá trị trung vị của nhà (MEDV) dựa trên các đặc trưng kinh tế – xã hội và cơ sở hạ tầng (CRIM, ZN, INDUS, CHAS, NOX, …).  
- **Ngôn ngữ**: Python (NumPy, Pandas, Matplotlib, Seaborn, scikit-learn).  
- **Môi trường**: Google Colab.

## 2. Nội dung chính

1. **Tiền xử lý dữ liệu**  
   - Đọc file `housing.csv` với tên cột tương ứng.  
   - Xem thông tin, thống kê (`df.info()`, `df.describe()`).  
   - Khám phá outliers bằng **boxplot** và **phân phối**.  
   - Loại bỏ một số outliers (VD: `MEDV >= 50`) để cải thiện chất lượng dữ liệu.  
   - Chuyển đổi (log transform) cho các biến skewed (CRIM, ZN, B, …) nhằm giảm độ lệch.

2. **Khám phá mối quan hệ**  
   - Sử dụng **heatmap** để xem tương quan giữa các biến.  
   - Chuẩn hóa dữ liệu (MinMaxScaler) cho một số biến quan trọng (LSTAT, PTRATIO, TAX, RM, NOX, …).  
   - Vẽ **regplot** để xem mối quan hệ tuyến tính/phi tuyến giữa các biến và giá nhà (MEDV).

3. **Xây dựng & đánh giá mô hình**  
   - Chia tập dữ liệu (hoặc dùng cross-validation KFold = 10).  
   - Thử nhiều mô hình:  
     - **LinearRegression**  
     - **Ridge** (có/không PolynomialFeatures)  
     - **SVR**  
     - **DecisionTreeRegressor**  
     - **KNeighborsRegressor**  
     - **GradientBoostingRegressor**  
   - Đánh giá bằng **R^2**, **MSE**, **MAE**:
     - MSE (Mean Squared Error)  
     - MAE (Mean Absolute Error)  
     - R^2 (Coefficient of Determination)

4. **Kết quả & Nhận xét**  
   - **SVR** (kernel RBF) cho kết quả tốt nhất với R^2 cao và MSE/MAE thấp.  
   - Ridge + PolynomialFeatures cũng cải thiện so với LinearRegression cơ bản.  
   - Decision Tree và KNN kém ổn định hơn, phụ thuộc vào tham số (max_depth, n_neighbors,…).  
   - Gradient Boosting đạt kết quả tốt, nhưng tùy vào learning_rate, max_depth.

## 3. Cấu trúc Notebook

- **Phần 1**: Import thư viện, đọc dữ liệu, gán tên cột.  
- **Phần 2**: Tiền xử lý (loại outliers, log transform).  
- **Phần 3**: Xây dựng mô hình, cross-validation, in kết quả.  
- **Phần 4**: So sánh mô hình, biểu đồ boxplot (MSE), chọn mô hình tối ưu.

## 4. Hướng dẫn chạy

1. **Clone** hoặc **download** dự án:  
   ```bash
   git clone https://github.com/your_username/Boston_Housing.git
   ```
2. **Mở notebook** `Boston_Housing_ipynb` trong Google Colab hoặc Jupyter Notebook.  
3. Cập nhật đường dẫn `df = pd.read_csv('.../housing.csv')` nếu cần.  
4. Chạy lần lượt các cell để xem kết quả phân tích và dự đoán.

## 5. Kết quả chính

- **Sau khi loại bỏ outliers và biến đổi log**:  
  - Dữ liệu ít skewed hơn, mô hình dễ fitting.  
- **SVR** với kernel RBF:  
  - R^2 cao nhất, MSE & MAE thấp nhất qua cross-validation (10-fold).  
  - Tổng quan, dự đoán giá nhà tốt nhất trong các mô hình thử nghiệm.  
- Các mô hình khác như **Ridge** (có PolynomialFeatures), **Gradient Boosting** cũng cho kết quả khá tốt.

## 6. Lưu ý & Phát triển thêm

- **Xóa outliers**:  
  - Cân nhắc khi outliers phản ánh thực tế.  
- **Hyperparameter Tuning**:  
  - Dùng GridSearchCV hoặc RandomizedSearchCV để tối ưu tham số cho SVR, Gradient Boosting, v.v.  
- **Thêm biến**:  
  - Nếu có thêm dữ liệu kinh tế – xã hội, hạ tầng, có thể nâng cao hiệu năng mô hình.

## 7. Tham khảo

- [Boston Housing dataset - UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Housing)  
- [Scikit-learn Documentation](https://scikit-learn.org/stable/documentation.html)

---

### Tác giả

- **Họ tên**: Bùi Thị Thanh Vân
- **Email**: thanh.van19062004@gmail.com
- **Liên hệ**: Mọi thắc mắc hoặc đóng góp vui lòng mở **issue** hoặc liên hệ email trên.
