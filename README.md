<div align="center">

# 🌊 SalinityCygnss

### Giám sát xâm nhập mặn bằng dữ liệu CYGNSS và Học Máy

*Ứng dụng công nghệ GNSS-Reflectometry và Machine Learning để lập bản đồ xâm nhập mặn tại Đồng Bằng Sông Cửu Long*

<br>

[![CYGNSS](https://img.shields.io/badge/CYGNSS-Satellite%20Data-0066cc?style=for-the-badge&logo=satellite)](https://github.com/quanguet0409/SalinityCygnss)
[![Machine Learning](https://img.shields.io/badge/ML-Random%20Forest%20|%20XGBoost%20|%20CatBoost-00cc66?style=for-the-badge&logo=tensorflow)](https://github.com/quanguet0409/SalinityCygnss)
[![Python](https://img.shields.io/badge/Python-3.8+-ff9900?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-red?style=for-the-badge)](LICENSE)

<br>

**[📌 Giới Thiệu](#-giới-thiệu)** |
**[🌐 Demo App](#-demo-app)** |
**[🔄 Quy Trình](#-quy-trình-nghiên-cứu)** |
**[🚀 Cài Đặt](#-cài-đặt)** |
**[💻 Sử Dụng](#-sử-dụng)** |
**[🤖 Mô Hình](#-các-mô-hình)** |
**[📊 Kết Quả](#-kết-quả)** |
**[📚 Nguồn Dữ Liệu](#-nguồn-dữ-liệu)**

---

[English](README.en.md) | **Tiếng Việt**

</div>

<br>

<div align="center">

## 📌 Giới Thiệu

</div>

**SalinityCygnss** khai thác dữ liệu **CYGNSS (Cyclone Global Navigation Satellite System)** - công nghệ GNSS-Reflectometry kết hợp các thuật toán **Machine Learning** tiên tiến để lập bản đồ và dự đoán xâm nhập mặn tại Đồng Bằng Sông Cửu Long.

### 📍 Các Khu Vực Nghiên Cứu

1. **ĐBSCL 2025** 
2. **Trà Vinh 2024** 
3. **Bến Tre 2020** 
4. **Bạc Liêu 2019**

### 🎯 Ý Nghĩa Nghiên Cứu

> Xâm nhập mặn là một trong những thách thức lớn nhất tại ĐBSCL, ảnh hưởng trực tiếp đến **19 triệu dân** và nguồn lương thực quốc gia.

**Nghiên cứu cung cấp:**

```diff
+ Giải pháp giám sát, chi phí thấp
+ Hỗ trợ quy hoạch nông nghiệp và quản lý tài nguyên nước
```

<br>

---

<div align="center">

## 🌐 Demo App

</div>

<div align="center">

### 🚀 Trải Nghiệm Ngay

**Xem bản đồ xâm nhập mặn tương tác trên Google Earth Engine**

<br>

[![Demo App](https://img.shields.io/badge/🌍_Xem_Demo_App-Earth_Engine-4285F4?style=for-the-badge&logo=google-earth&logoColor=white)](https://ee-hanoi688.projects.earthengine.app/view/soil-salinity)

<br>

> 📍 **Chức năng:** Xem bản đồ dự đoán xâm nhập mặn theo tháng, so sánh các mô hình, và khám phá dữ liệu thực địa

</div>

<br>

---

<div align="center">

## 🔄 Quy Trình Nghiên Cứu

</div>

<div align="center">

![Sơ đồ quy trình](assets/flowchart.png)

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

1. Mở Jupyter Notebook tương ứng:
   ```bash
   jupyter notebook Mekong2025/Model/XGB.ipynb
   ```

2. Chạy từng cell theo thứ tự

3. Kết quả dự đoán sẽ được lưu trong `Model Results/`

### Quy Trình Trong Notebook

1. Load dữ liệu → 2. Tiền xử lý → 3. Huấn luyện → 4. Đánh giá → 5. Dự đoán → 6. Trực quan hóa

---

## 📂 Cấu Trúc Nghiên Cứu

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

<br>

---

<div align="center">

## 📊 Kết Quả

</div>

### 📈 Hiệu Suất Mô Hình

Ba mô hình machine learning được huấn luyện và đánh giá trên **tập kiểm tra**:

<div align="center">

| 📊 Chỉ Số | 📝 Ý Nghĩa | ✅ Giá Trị Tốt |
|:--------:|:-----------|:--------------:|
| **R** | Hệ số tương quan | ↑ Càng gần 1 |
| **RMSE** | Sai số bình phương trung bình | ↓ Càng nhỏ |
| **MAE** | Sai số tuyệt đối trung bình | ↓ Càng nhỏ |

</div>

<br>

### 🏆 Bảng So Sánh Hiệu Suất Chi Tiết

<div align="center">

<table>
<thead>
  <tr>
    <th rowspan="2">Thuật toán</th>
    <th colspan="3">Tập huấn luyện</th>
    <th colspan="3">Tập kiểm tra</th>
  </tr>
  <tr>
    <th>RMSE (dS/m)</th>
    <th>MAE (dS/m)</th>
    <th>R</th>
    <th>RMSE (dS/m)</th>
    <th>MAE (dS/m)</th>
    <th>R</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Random Forest</td>
    <td>1.59</td>
    <td>0.77</td>
    <td>0.94</td>
    <td>2.73</td>
    <td>1.37</td>
    <td>0.78</td>
  </tr>
  <tr>
    <td><strong>XGBoost</strong> ⭐</td>
    <td><strong>1.37</strong></td>
    <td><strong>0.69</strong></td>
    <td><strong>0.95</strong></td>
    <td><strong>2.55</strong></td>
    <td><strong>1.31</strong></td>
    <td><strong>0.81</strong></td>
  </tr>
  <tr>
    <td>CatBoost</td>
    <td>1.72</td>
    <td>0.96</td>
    <td>0.94</td>
    <td>2.65</td>
    <td>1.36</td>
    <td>0.80</td>
  </tr>
</tbody>
</table>

</div>

> **Ghi chú**: 
> - ⭐ = Mô hình tốt nhất (XGBoost có RMSE thấp nhất và R cao nhất trên tập kiểm tra)

<br>

### 📍 Dữ Liệu Trạm Đo Mặn Thực Địa

<div align="center">

> 7 trạm đo mặn thực địa phân bố khắp Đồng Bằng Sông Cửu Long

</div>

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

<br>

### 💡 Nhận Xét

<div align="center">

| Mô Hình | Đánh Giá |
|:-------:|:---------|
| **XGBoost** 🥇 | Kết quả tốt nhất với RMSE thấp nhất (2.55 dS/m) và R cao nhất (0.81) |
| **Random Forest** 🥈 | Độ ổn định cao nhưng RMSE cao hơn (2.73 dS/m) |
| **CatBoost** 🥉 | Cân bằng giữa hiệu suất và thời gian huấn luyện |

</div>



<br>

---

<div align="center">

## 🗺️ Bản Đồ Xâm Nhập Mặn

</div>

### 📅 Theo Dõi Biến Đổi Theo Thời Gian (Tháng 1-5/2025)

<div align="center">

*Kết quả dự đoán xâm nhập mặn cho 5 tháng đầu năm 2025 tại ĐBSCL*

**Nhấp vào từng mô hình để xem chi tiết**

</div>

<details>
<summary><b>CatBoost - Nhấp để xem 5 tháng</b></summary>

![Tháng 1](assets/CB_1.jpg)
![Tháng 2](assets/CB_2.jpg)
![Tháng 3](assets/CB_3.jpg)
![Tháng 4](assets/CB_4.jpg)
![Tháng 5](assets/CB_5.jpg)

</details>

<details>
<summary><b>Random Forest - Nhấp để xem 5 tháng</b></summary>

![Tháng 1](assets/RF_1.jpg)
![Tháng 2](assets/RF_2.jpg)
![Tháng 3](assets/RF_3.jpg)
![Tháng 4](assets/RF_4.jpg)
![Tháng 5](assets/RF_5.jpg)

</details>

<details>
<summary><b>XGBoost - Nhấp để xem 5 tháng</b></summary>

![Tháng 1](assets/XGB_1.jpg)
![Tháng 2](assets/XGB_2.jpg)
![Tháng 3](assets/XGB_3.jpg)
![Tháng 4](assets/XGB_4.jpg)
![Tháng 5](assets/XGB_5.jpg)

</details>

### 🎯 Features Quan Trọng

Các features được sử dụng bao gồm:
- **CYGNSS Data**: SR (Surface Reflectivity)
- **Spectral Indices**: NDVI, NDSI, Salinity Index (SI1-SI5), SWIR1, SWIR2
- **Environmental**: SM (Soil Moisture), LST (Land Surface Temperature), DEM
- **Soil Properties**: Sand, Clay, Bulk Density
- **Land Use**: LULC

*Kết quả chi tiết và bản đồ các tháng khác có trong `Mekong2025/Results/`*

> 📌 **Dữ liệu khác:** Nếu cần các dữ liệu bổ sung hoặc dữ liệu thô, vui lòng liên hệ qua email: **quanghieuminh14@gmail.com**

---

## 📚 Nguồn Dữ Liệu

<div align="center">

![SAE Logo](assets/sae_logo.png)

**VIỆN CÔNG NGHỆ HÀNG KHÔNG VŨ TRỤ**  
Trường Đại Học Công Nghệ - Đại Học Quốc Gia Hà Nội

</div>

### Dữ Liệu Chính

**Dữ Liệu CYGNSS**
- Cung cấp: **ThS. Hoàng Tích Phúc** - phucth@vnu.edu.vn
- Đơn vị: Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội

**Dữ Liệu Điểm Mặn Thực Địa**
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
- TS. Hà Minh Cường và ThS. Hoàng Tích Phúc
- Viện Công Nghệ Hàng Không Vũ Trụ - ĐH Công Nghệ - ĐHQG Hà Nội

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
