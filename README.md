# DataFlow — HCMUT Master's Data Analytics Hub

Trang Hub dự án & Báo cáo đồ án môn **Nền tảng lập trình cho phân tích và trực quan dữ liệu (CO5177)** — Trường Đại học Bách Khoa TP.HCM (HCMUT).

**Tác giả / Sinh viên:** Nguyễn Thị Hồng Hạnh (Student ID: 2670306)
**Giảng viên hướng dẫn:** TS. Lê Thành Sách

---

## 📖 Giới thiệu Báo cáo Đồ án

### 1. Bài toán dữ liệu Văn bản (Text Track) — BBC News Classification
- **Nguồn dữ liệu:** BBC News Dataset (2,225 bài báo tiếng Anh).
- **Mục tiêu:** Phân loại đa lớp (Multiclass Classification) cho 5 chủ đề: *Sport*, *Business*, *Politics*, *Tech*, *Entertainment*.
- **Kết quả mô hình:** Multinomial Naive Bayes + TF-IDF đạt **Macro F1-Score = 0.974** và **Accuracy = 97.5%**.
- **Tài nguyên:** Trang web báo cáo `text-eda.html` và file PDF chi tiết `reports/text-bbc-eda-report.pdf`.

### 2. Bài toán dữ liệu Dạng bảng (Tabular Track) — NASA Kepler Exoplanet Detection
- **Nguồn dữ liệu:** NASA Exoplanet Archive (9,564 quan sát, 30 đặc trưng vật lý).
- **Mục tiêu:** Phân loại 3 nhóm tín hiệu hành tinh (*Confirmed*, *Candidate*, *False Positive*).
- **Kết quả mô hình:** Balanced Random Forest nâng Macro F1 từ **0.558** lên **0.758**.
- **Tài nguyên:** Trang web báo cáo `tabular-eda.html`.

---

## 📁 Cấu trúc thư mục dự án

```text
.
├── index.html                   # Landing page Hub giới thiệu tổng quan đồ án (Đã gộp CSS)
├── text-eda.html                # Báo cáo phân tích dữ liệu văn bản tiếng Anh (BBC News)
├── tabular-eda.html             # Báo cáo phân tích dữ liệu dạng bảng (NASA Kepler KOI)
├── dataset.csv                  # Bộ dữ liệu BBC News (2,225 bài báo tiếng Anh, 5 nhãn)
├── koi_cumulative.csv           # Bộ dữ liệu NASA Kepler KOI (9,564 dòng, 30 cột)
├── reports/
│   ├── text-bbc-eda-report.pdf  # Báo cáo PDF phân tích dữ liệu văn bản BBC News
│   └── tabular-koi-eda-report.pdf # Báo cáo PDF phân tích dữ liệu dạng bảng Kepler KOI
└── README.md                    # File giới thiệu báo cáo & Hướng dẫn sử dụng
