# 🛰️ สัปดาห์ที่ 11: การจัดการข้อมูลขนาดใหญ่ด้วย GEEmap

## วิชา GE 234 Basic Programming for Geographers

| | |
|---|---|
| **วันที่** | 16 มีนาคม 2569 |
| **สถานะ** | ⏳ ยังไม่สอน |
| **หัวข้อ** | Google Earth Engine in Python |
| **งานส่ง** | 📋 Lab 4: การประมวลผลข้อมูลด้วย NumPy และ GeoPandas |

---

## 📖 เนื้อหาที่เรียน

### 1. Google Earth Engine คืออะไร?

| | |
|---|---|
| **900+ Dataset** | Landsat, Sentinel, MODIS, ERA5 ฯลฯ |
| **Cloud Processing** | ประมวลผลบน Server ไม่ต้องดาวน์โหลด |
| **40+ ปี Archive** | ข้อมูลย้อนหลังตั้งแต่ปี 1984 |

**geemap** = Python + GEE — ใช้ GEE ใน Python/Jupyter ได้สะดวก สร้างแผนที่ Interactive วิเคราะห์ข้อมูลดาวเทียมได้โดยไม่ต้องดาวน์โหลด

### 2. การตั้งค่าและเชื่อมต่อ
1. สร้าง GEE Account ที่ earthengine.google.com
2. ติดตั้ง `pip install geemap`
3. Authenticate ด้วย `ee.Authenticate()`
4. Initialize ด้วย `ee.Initialize(project='...')`

### 3. โหลดภาพดาวเทียม

| | Landsat 9 | Sentinel-2 |
|---|---|---|
| **ความละเอียด** | 30 เมตร | 10 เมตร |
| **รอบถ่าย** | 16 วัน | 5 วัน |
| **ข้อมูลย้อนหลัง** | 1984 - ปัจจุบัน | 2015 - ปัจจุบัน |
| **Band** | 11 bands | 13 bands |
| **Collection ID** | `LANDSAT/LC09/C02/T1_L2` | `COPERNICUS/S2_SR_HARMONIZED` |

ใช้ `.filterBounds()`, `.filterDate()`, `.filter(ee.Filter.lt("CLOUD_COVER", 20))` เพื่อกรองข้อมูล

### 4. NDVI — ดัชนีพืชพรรณ

**NDVI = (NIR − Red) / (NIR + Red)** — ค่า -1 ถึง 1

| ช่วงค่า | ความหมาย |
|---------|----------|
| < 0 | น้ำ |
| 0 – 0.2 | ดิน/เมือง |
| 0.2 – 0.5 | ทุ่งหญ้า/เกษตร |
| > 0.5 | ป่าหนาแน่น |

### 5. การวิเคราะห์เชิงเวลา (Time Series)
ดึง NDVI รายเดือนย้อนหลัง เพื่อดูแนวโน้มการเปลี่ยนแปลง — ฤดูแล้ง NDVI ต่ำ (พืชน้อย) ฤดูฝน NDVI สูง (พืชเขียว)

### 6. Export ข้อมูลจาก GEE

| วิธี | เหมาะกับ | ฟังก์ชัน |
|------|----------|---------|
| Google Drive | พื้นที่ใหญ่ | `ee.batch.Export.image.toDrive()` |
| ดาวน์โหลดตรง | พื้นที่เล็ก | `geemap.ee_export_image()` |

### 7. Median Composite
รวมหลายภาพเข้าด้วยกัน ลดผลกระทบจากเมฆด้วย `.median()`

---

## 📝 แบบฝึกหัด

1. โหลดภาพ Sentinel-2 ของจังหวัดบ้านเกิด แสดง True Color
2. คำนวณ NDVI แสดงบนแผนที่พร้อม Colorbar
3. เปรียบเทียบ NDVI ฤดูแล้ง vs ฤดูฝน
4. สร้าง Median Composite ปี 2024 แล้ว Export เป็น GeoTIFF

---

## 📂 ไฟล์ในโฟลเดอร์นี้

| ไฟล์ | รายละเอียด |
|------|-----------|
| `Week11_GEEmap_Lecture.pptx` | สไลด์บรรยาย |
| `Week11_GEEmap_GoogleEarthEngine.ipynb` | Notebook Workshop |
| `Lab4_GE234_NumPy_GeoPandas.ipynb` | Lab 4 |
| `README.md` | ไฟล์นี้ |

---

## 🔗 สัปดาห์ถัดไป
**Week 12:** การสร้างแผนที่ 3 มิติด้วย MapLibre — 3D Terrain, 3D Buildings, WebGL, Interactive 3D Map

---

*ภาควิชาภูมิศาสตร์ คณะศิลปศาสตร์ มหาวิทยาลัยธรรมศาสตร์*
