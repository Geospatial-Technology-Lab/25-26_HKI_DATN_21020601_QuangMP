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

## Giới Thiệu

**SalinityCygnss** khai thác dữ liệu **CYGNSS (Cyclone Global Navigation Satellite System)** - công nghệ GNSS-Reflectometry kết hợp các thuật toán **Machine Learning** tiên tiến (Random Forest, XGBoost, CatBoost) để lập bản đồ và dự đoán xâm nhập mặn tại Đồng Bằng Sông Cửu Long.

### Các Khu Vực Nghiên Cứu

- **Đồng Bằng Sông Cửu Long 2025** - Nghiên cứu toàn diện (5 tháng: 1-5/2025)
- **Trà Vinh 2024** - Phân tích khu vực
- **Bến Tre 2020** - Dữ liệu so sánh
- **Bạc Liêu 2019** - Baseline

### Ý Nghĩa Nghiên Cứu

Xâm nhập mặn là một trong những thách thức lớn nhất tại ĐBSCL, ảnh hưởng trực tiếp đến 19 triệu dân và nguồn lương thực quốc gia. Dự án cung cấp:
- Giải pháp giám sát real-time, chi phí thấp
- Bản đồ độ phân giải không gian cao (30m)
- Hỗ trợ quy hoạch nông nghiệp và quản lý tài nguyên nước

---

## Quy Trình Nghiên Cứu

<div align="center">

![Sơ đồ quy trình](flowchart.png)

</div>

### Các Bước Chính

1. **Thu Thập Dữ Liệu**
   - Dữ liệu CYGNSS: SR (Surface Reflectivity)
   - Viễn thám: NDVI, NDSI, LST, LULC
   - Địa hình: DEM (Digital Elevation Model)
   - Environmental: SM (Soil Moisture)
   - Thổ nhưỡng: Sand, Clay, Bulk Density
   - Salinity Index: SI1-SI5

2. **Dữ Liệu Thực Địa** → Đo điểm mặn thực địa EC (dS/m)

3. **Tiền Xử Lý** → Chuẩn hóa, tạo training/testing dataset (70/30)

4. **Mô Hình Hóa** → Random Forest, XGBoost, CatBoost

5. **Đánh Giá** → R (Correlation), RMSE, MAE, K-Fold Validation

6. **Xuất Kết Quả** → Bản đồ xâm nhập mặn theo tháng (1-5/2025)

---

## Cài Đặt

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

## Sử Dụng

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

## Cấu Trúc Dự Án

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

## Các Mô Hình

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

## Kết Quả

### Hiệu Suất Mô Hình

Ba mô hình (RF, XGBoost, CatBoost) được đánh giá dựa trên:
- **R (Correlation Coefficient)** - Hệ số tương quan
- **RMSE (Root Mean Square Error)** - Sai số bình phương trung bình
- **MAE (Mean Absolute Error)** - Sai số tuyệt đối trung bình

### Bản Đồ Xâm Nhập Mặn (Tháng 1-5/2025)

#### CatBoost

````carousel
![Tháng 1](CB_1.jpg)
<!-- slide -->
![Tháng 2](CB_2.jpg)
<!-- slide -->
![Tháng 3](CB_3.jpg)
<!-- slide -->
![Tháng 4](CB_4.jpg)
<!-- slide -->
![Tháng 5](CB_5.jpg)
````

#### Random Forest

````carousel
![Tháng 1](RF_1.jpg)
<!-- slide -->
![Tháng 2](RF_2.jpg)
<!-- slide -->
![Tháng 3](RF_3.jpg)
<!-- slide -->
![Tháng 4](RF_4.jpg)
<!-- slide -->
![Tháng 5](RF_5.jpg)
````

#### XGBoost

````carousel
![Tháng 1](XGB_1.jpg)
<!-- slide -->
![Tháng 2](XGB_2.jpg)
<!-- slide -->
![Tháng 3](XGB_3.jpg)
<!-- slide -->
![Tháng 4](XGB_4.jpg)
<!-- slide -->
![Tháng 5](XGB_5.jpg)
````

### Features Quan Trọng

Các features được sử dụng bao gồm:
- **CYGNSS Data**: SR (Surface Reflectivity)
- **Spectral Indices**: NDVI, NDSI, Salinity Index (SI1-SI5)
- **Environmental**: SM (Soil Moisture), LST (Land Surface Temperature), DEM
- **Soil Properties**: Sand, Clay, Bulk Density
- **Land Use**: LULC, SWIR1, SWIR2

*Kết quả chi tiết và bản đồ các tháng khác có trong `Mekong2025/Results/`*

---

## Nguồn Dữ Liệu

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

## Giấy Phép

Dự án sử dụng giấy phép MIT - xem [LICENSE](LICENSE).

---

## Liên Hệ

**Tác Giả**: Phạm Minh Quang  
**Email**: quanghieuminh14@gmail.com  
**Tổ Chức**: Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội

**GitHub**: [https://github.com/quanguet0409/SalinityCygnss](https://github.com/quanguet0409/SalinityCygnss)

---

## Lời Cảm Ơn

- NASA CYGNSS mission
- TS. Hà Minh Cường và ThS. Hoàng Tích Phúc
- Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội
- Đội ngũ thực địa và cộng đồng mã nguồn mở

---

## Trích Dẫn

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

<div align="center">

⭐ **Nếu thấy hữu ích, hãy cho repo một ngôi sao!** ⭐

*Phát triển vì nông nghiệp bền vững tại Đồng Bằng Sông Cửu Long*

</div>