# SalinityCygnss

<div align="center">

![CYGNSS](https://img.shields.io/badge/CYGNSS-Satellite%20Data-blue?style=for-the-badge)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Prediction-green?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-Jupyter-orange?style=for-the-badge)

**Dự Đoán Xâm Nhập Mặn Bằng Dữ Liệu CYGNSS và Học Máy**

*Ứng dụng công nghệ GNSS-R và Machine Learning để lập bản đồ xâm nhập mặn tại Đồng Bằng Sông Cửu Long*

---

[Giới Thiệu](#giới-thiệu) • [Quy Trình](#quy-trình-nghiên-cứu) • [Cài Đặt](#cài-đặt) • [Sử Dụng](#sử-dụng) • [Mô Hình](#các-mô-hình) • [Nguồn Dữ Liệu](#nguồn-dữ-liệu)

</div>

---

## 📌 Giới Thiệu

**SalinityCygnss** khai thác dữ liệu **CYGNSS (Cyclone Global Navigation Satellite System)** - công nghệ GNSS-Reflectometry kết hợp các thuật toán **Machine Learning** tiên tiến (Random Forest, XGBoost, CatBoost) để lập bản đồ và dự đoán xâm nhập mặn tại Đồng Bằng Sông Cửu Long.

### Các Khu Vực Nghiên Cứu

- **Đồng Bằng Sông Cửu Long 2025** 
- **Trà Vinh 2024** 
- **Bến Tre 2020** 
- **Bạc Liêu 2019** 

### Ý Nghĩa Nghiên Cứu

Xâm nhập mặn là một trong những thách thức lớn nhất tại ĐBSCL, ảnh hưởng trực tiếp đến 19 triệu dân và nguồn lương thực quốc gia. Dự án cung cấp:
- Giải pháp giám sát real-time, chi phí thấp
- Bản đồ độ phân giải không gian cao (30m)
- Hỗ trợ quy hoạch nông nghiệp và quản lý tài nguyên nước

---

## 🔄 Quy Trình Nghiên Cứu

<div align="center">

![Sơ đồ quy trình](flowchart.png)

*Hình 1: Quy trình nghiên cứu xâm nhập mặn sử dụng CYGNSS và Machine Learning*

</div>

### Các Bước Chính

1. **Thu Thập Dữ Liệu**
   - Dữ liệu CYGNSS: SR (Surface Reflectivity)
   - Viễn thám: NDVI, NDSI, LST, LULC
   - Địa hình: DEM (Digital Elevation Model)
   - Environmental: SM (Soil Moisture)
   - Thổ nhưỡng: Sand, Clay, Bulk Density
   - Salinity Index: SI1-SI5

2. **Dữ Liệu Thực Địa** → Đo điểm mặn thực địa EC (dS/m), Trạm đo quan trắc

3. **Tiền Xử Lý** → Chuẩn hóa

4. **Mô Hình Hóa** → Random Forest, XGBoost, CatBoost

5. **Đánh Giá** → R (Correlation), RMSE, MAE, K-Fold Validation

6. **Xuất Kết Quả** → Bản đồ xâm nhập mặn theo tháng (1-5/2025)

---

## 🚀 Cài Đặt

### Yêu Cầu

- Python 3.8+
- Jupyter Notebook
- Git

### Cài Đặt Nhanh

```bash
git clone https://github.com/quanguet0409/SalinityCygnss.git
cd SalinityCygnss
pip install -r requirements.txt
```

### Thư Viện Chính

`numpy` • `pandas` • `scikit-learn` • `xgboost` • `catboost` • `matplotlib` • `seaborn` • `geopandas` • `rasterio`

---

## 💻 Sử Dụng

### Chạy Mô Hình

```bash
cd Mekong2025/Model
jupyter notebook
```

Chọn một trong ba notebook:
- `RF.ipynb` - Random Forest
- `XGB.ipynb` - XGBoost  
- `CB.ipynb` - CatBoost

### Quy Trình Trong Notebook

1. Load dữ liệu → 2. Tiền xử lý → 3. Huấn luyện → 4. Đánh giá → 5. Dự đoán → 6. Trực quan hóa

---

## 📂 Cấu Trúc Dự Án

```
SalinityCygnss/
├── Mekong2025/              # ĐBSCL 2025 (mới nhất)
│   ├── Data/                # 91 files
│   ├── Model/               # RF, XGB, CB notebooks
│   ├── Model Results/       # 15 output files
│   ├── Results/             # Bản đồ dự đoán
│   └── SHP/                 # Shapefiles ĐBSCL
├── TraVinh2024/             # Trà Vinh
│   ├── Data/                # 19 files
│   └── SHP/                 # 8 shapefiles
├── BenTre2020/              # Bến Tre
│   ├── Data/                # 19 files
│   ├── Model/               # 3 models
│   └── Results/             # 3 outputs
├── BacLieu2019/             # Bạc Liêu
├── LICENSE
├── README.md
└── flowchart.png
```

---

## 🤖 Các Mô Hình

### 1. Random Forest (RF)
Tổng hợp nhiều cây quyết định, kháng overfitting, xử lý mối quan hệ phi tuyến.

### 2. XGBoost (XGB)
Gradient boosting hiệu suất cao, điều chuẩn tự động, xử lý missing values.

### 3. CatBoost (CB)
Xử lý đặc trưng phân loại tốt, hỗ trợ GPU, tốc độ dự đoán nhanh.

### Đánh Giá Mô Hình

- **R** - Hệ số tương quan
- **RMSE** - Root Mean Square Error
- **MAE** - Mean Absolute Error
- **K-Fold Validation** - Kiểm định chéo

---

## 📊 Kết Quả

### Hiệu Suất Mô Hình

Ba mô hình machine learning được huấn luyện và đánh giá trên tập kiểm tra (30% dữ liệu) với các chỉ số:

| Chỉ Số | Ý Nghĩa | Giá Trị Tốt |
|--------|---------|-------------|
| **R** | Hệ số tương quan (Correlation Coefficient) | Càng gần 1 càng tốt |
| **RMSE** | Sai số bình phương trung bình (Root Mean Square Error) | Càng nhỏ càng tốt |
| **MAE** | Sai số tuyệt đối trung bình (Mean Absolute Error) | Càng nhỏ càng tốt |

### Bảng So Sánh Hiệu Suất Chi Tiết

<div align="center">

| Thuật toán | Tập huấn luyện ||| Tập kiểm tra |||
|:--------|:---:|:---:|:---:|:---:|:---:|:---:|
| | **RMSE (dS/m)** | **MAE (dS/m)** | **R** | **RMSE (dS/m)** | **MAE (dS/m)** | **R** |
| Random Forest | 1.59 | 0.77 | 0.94 | 2.73 | 1.37 | 0.78 |
| **XGBoost** ⭐ | **1.37** | **0.69** | **0.95** | **2.55** | **1.31** | **0.81** |
| CatBoost | 1.72 | 0.96 | 0.94 | 2.65 | 1.36 | 0.80 |

</div>

> **Ghi chú**: 
> - ⭐ = Mô hình tốt nhất (XGBoost có RMSE thấp nhất và R cao nhất trên tập kiểm tra)
> - Kết quả trên là trung bình cho 5 tháng (1-5/2025)
> - Dữ liệu: 70% huấn luyện, 30% kiểm tra

### Dữ Liệu Trạm Đo Mặn Thực Địa

<div align="center">

| Tên Trạm | Tỉnh/Phương | Tháng 1 | Tháng 2 | Tháng 3 | Tháng 4 | Tháng 5 |
|:----------|:------------|:--------:|:--------:|:--------:|:--------:|:--------:|
| Tuyên Nhơn | Long An | 0.033 | 0.2 | 0.37 | 0.23 | 0.2 |
| Bến Trại | Bến Tre | 18.5 | 18.67 | 23.43 | 18.73 | 19.6 |
| Đại Ngãi | Sóc Trăng | 3.4 | 6.77 | 7.37 | 4.6 | 1.9 |
| Gò Quao | Kiên Giang | 2.3 | 3.73 | 2.33 | 4.33 | 3.6 |
| Văm Kénh | Tiền Giang | 21.43 | 21.53 | 21.8 | 20.2 | 17.6 |
| Trà Kha | Trà Vinh | 15.6 | 17.97 | 16.23 | 13.03 | 12.1 |
| Sông Đốc | Cà Mau | 30.2 | 31 | 33.47 | 33.77 | 34.3 |

*Bảng: Giá trị đo mặn tại các trạm (dS/m)*

</div>

### Nhận Xét

- **XGBoost** cho kết quả tốt nhất với RMSE thấp nhất (2.55 dS/m) và R cao nhất (0.81) trên tập kiểm tra
- **Random Forest** có độ ổn định cao nhưng RMSE cao hơn (2.73 dS/m)
- **CatBoost** cân bằng giữa hiệu suất và thời gian huấn luyện



---

## 🗺️ Bản Đồ Xâm Nhập Mặn

### Theo Dõi Biến Đổi Theo Thời Gian (Tháng 1-5/2025)

Kết quả dự đoán xâm nhập mặn cho 5 tháng đầu năm 2025 tại ĐBSCL.

<details>
<summary><b>CatBoost - Nhấp để xem 5 tháng</b></summary>

![Tháng 1](CB_1.jpg)
![Tháng 2](CB_2.jpg)
![Tháng 3](CB_3.jpg)
![Tháng 4](CB_4.jpg)
![Tháng 5](CB_5.jpg)

</details>

<details>
<summary><b>Random Forest - Nhấp để xem 5 tháng</b></summary>

![Tháng 1](RF_1.jpg)
![Tháng 2](RF_2.jpg)
![Tháng 3](RF_3.jpg)
![Tháng 4](RF_4.jpg)
![Tháng 5](RF_5.jpg)

</details>

<details>
<summary><b>XGBoost - Nhấp để xem 5 tháng</b></summary>

![Tháng 1](XGB_1.jpg)
![Tháng 2](XGB_2.jpg)
![Tháng 3](XGB_3.jpg)
![Tháng 4](XGB_4.jpg)
![Tháng 5](XGB_5.jpg)

</details>

### 🎯 Features Quan Trọng

Các features được sử dụng bao gồm:
- **CYGNSS Data**: SR (Surface Reflectivity)
- **Spectral Indices**: NDVI, NDSI, Salinity Index (SI1-SI5)
- **Environmental**: SM (Soil Moisture), LST (Land Surface Temperature), DEM
- **Soil Properties**: Sand, Clay, Bulk Density
- **Land Use**: LULC, SWIR1, SWIR2

*Kết quả chi tiết và bản đồ các tháng khác có trong `Mekong2025/Results/`*

---

## 📚 Nguồn Dữ Liệu

<div align="center">

![SAE Logo](sae_logo.png)

**VIỆN CÔNG NGHỆ HÀNG KHÔNG VŨ TRỤ**  
Trường Đại Học Công Nghệ - Đại Học Quốc Gia Hà Nội

</div>

### Dữ Liệu Chính

**Dữ Liệu CYGNSS**
- Nguồn: NASA CYGNSS Level 1 Science Data Record
- Cung cấp: **ThS. Hoàng Tích Phúc** - phucth@vnu.edu.vn
- Đơn vị: Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội

**Dữ Liệu Điểm Mặn Thực Địa**
- Đo đạc hiện trường và phân tích phòng thí nghiệm
- Cung cấp: **TS. Hà Minh Cường** - cuonghm@vnu.edu.vn
- Đơn vị: Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội

### Dữ Liệu Phụ Trợ

Mô hình số độ cao (DEM) • Sử dụng đất/lớp phủ • Tính chất đất • Biến khí hậu

---

## 📜 Giấy Phép

Dự án sử dụng giấy phép MIT - xem [LICENSE](LICENSE).

---

## 📧 Liên Hệ

**Tác Giả**: Phạm Minh Quang  
**Email**: quanghieuminh14@gmail.com  
**Tổ Chức**: Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội

**GitHub**: [https://github.com/quanguet0409/SalinityCygnss](https://github.com/quanguet0409/SalinityCygnss)

---

## 🙏 Lời Cảm Ơn

- NASA CYGNSS mission
- TS. Hà Minh Cường và ThS. Hoàng Tích Phúc
- Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội
- Đội ngũ thực địa và cộng đồng mã nguồn mở

---

## 📖 Trích Dẫn

```bibtex
@software{SalinityCygnss2025,
  author = {Phạm Minh Quang},
  title = {SalinityCygnss: Dự Đoán Xâm Nhập Mặn Bằng Dữ Liệu CYGNSS và Học Máy},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/quanguet0409/SalinityCygnss}
}
```

---
