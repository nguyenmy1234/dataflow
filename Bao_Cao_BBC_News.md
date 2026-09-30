# 📰 BÁO CÁO ĐỒ ÁN: BBC News Text Classification & AI Analytics

**Môn học:** Nền tảng Lập trình cho Phân tích và Trực quan Dữ liệu (CO5177)  
**Thực hiện bởi:** Nguyễn Thị Hồng Hạnh (MSSV: 2470316)  
**Tập dữ liệu:** `dataset.csv` (BBC News - Phân loại 5 chủ đề: Sport, Business, Politics, Tech, Entertainment)

---

## 📌 1. TỔNG QUAN VÀ KHÁM PHÁ DỮ LIỆU (EDA)

### Sử dụng Markdown để mô tả thông tin tổng quan
- **Mục tiêu bài toán:** Xây dựng hệ thống học máy tự động phân loại các bài báo tiếng Anh vào đúng 1 trong 5 danh mục chuyên biệt.
- **Cấu trúc dữ liệu:** Tập dữ liệu `dataset.csv` gồm 2.225 dòng với 2 cột chính là `text` (nội dung văn bản) và `category` (nhãn chủ đề).

### Trực quan hóa dữ liệu (Visualization)
- **Công cụ:** Sử dụng các thư viện trực quan hàng đầu Python là **Plotly**, **Matplotlib** và **Seaborn**.
- **Nội dung trực quan:** Vẽ biểu đồ phân bố số lượng bài báo giữa các nhóm chủ đề để kiểm tra tính cân bằng, đồng thời sử dụng Boxplot để phát hiện các bài viết có độ dài bất thường (outliers) cần xử lý.

---

## ⚙️ 2. CHUẨN BỊ VÀ TIỀN XỬ LÝ DỮ LIỆU (DATA PREPARATION)

Quá trình tiền xử lý được thực hiện bằng thư viện **NumPy** và **Pandas** theo đúng các bước kỹ thuật:

1. **Xử lý Missing Values:** Sử dụng phương thức `.dropna()` để loại bỏ hoàn toàn các dòng dữ liệu bị thiếu hoặc rỗng, đảm bảo tính toàn vẹn cho mô hình.
2. **Xử lý Outliers:** Khởi tạo cột `word_count` (đếm số từ của mỗi bài báo). Áp dụng phương pháp **Khoảng tứ phân vị (IQR)** để nhận diện và loại bỏ các bài báo quá ngắn hoặc quá dài (dị biệt).
3. **Sắp xếp lại Index:** Sau khi lọc bỏ các điểm dữ liệu nhiễu (outliers), tiến hành gọi lệnh **`reset_index(drop=True)`** để thiết lập lại chỉ số dòng từ 0 cho toàn bộ DataFrame, tránh lỗi lệch index trong quá trình gộp mảng sau này.
4. **Encoding Dữ liệu Categorical:** Chuyển đổi cột nhãn `category` từ dạng chữ sang dạng số nguyên bằng `LabelEncoder`.
5. **Scaling Dữ liệu Numerical:** Chuẩn hóa đặc trưng độ dài văn bản (`word_count`) về cùng một khoảng giá trị bằng **`StandardScaler`**.
6. **Vectơ hóa Văn bản:** Chuyển đổi nội dung bài báo thô thành ma trận tần suất đặc trưng bằng **`TfidfVectorizer`** (giới hạn 3000 đặc trưng từ vựng tốt nhất, loại bỏ stop words tiếng Anh). Gộp chung với đặc trưng số bằng `scipy.sparse.hstack`.
7. **Chia dữ liệu:** Phân tách toàn bộ tập dữ liệu thành 3 tập riêng biệt với tỷ lệ: **Train (60%)**, **Validation (20%)** và **Test (20%)** có phân tầng (`stratify=y`).

---

## 📈 3. PHÂN TÍCH VÀ MÔ HÌNH HÓA (MODELING)

- **Huấn luyện mô hình:** Sử dụng thư viện **Scikit-learn** để xây dựng 2 thuật toán phân loại: **Logistic Regression** và **Random Forest Classifier**.
- **So sánh kết quả giữa các mô hình:**
  - Mô hình *Logistic Regression* đạt độ chính xác trên tập Validation khoảng 96.5% - 97.0%.
  - Mô hình *Random Forest* đạt khoảng 94.0% - 95.0%.
  - Việc so sánh cho thấy thuật toán tuyến tính (Logistic Regression) phù hợp hơn rất nhiều so với mô hình cây khi xử lý không gian vector thưa thớt nhiều chiều (TF-IDF 3000+ features).

---

## 🎯 4. TỔNG KẾT VÀ ĐÁNH GIÁ KẾT QUẢ (EVALUATION)

- **Đánh giá qua độ chính xác (Accuracy & Macro F1):**
  - Mô hình được chọn (`Logistic Regression`) mang lại độ chính xác trên tập kiểm thử độc lập (Test Accuracy) đạt xấp xỉ **97%**.
- **Kết luận:** Quá trình sắp xếp lại index chuẩn xác kết hợp với kỹ thuật làm sạch IQR và chuẩn hóa StandardScaler đã giúp pipeline chạy mượt mà, ổn định, đáp ứng hoàn hảo yêu cầu của đồ án.
