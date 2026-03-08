# 🗺️ สัปดาห์ที่ 10: การพัฒนาแผนที่ด้วย Leafmap

## วิชา GE 234 Basic Programming for Geographers

| | |
|---|---|
| **วันที่** | 9 มีนาคม 2569 |
| **สถานะ** | ⏳ ยังไม่สอน |
| **หัวข้อ** | Interactive Web Map for Geographers |
| **งานส่ง** | 📋 Code Repository #3 (ส่งก่อนสัปดาห์หน้า) |

---

## 📖 เนื้อหาที่เรียน

### 1. Leafmap คืออะไร?
Python Package สำหรับสร้าง Interactive GIS Map สร้างจาก ipyleaflet + folium รองรับ Basemap 100+ แบบ รองรับ GeoJSON, Shapefile, GeoTIFF ทำงานร่วมกับ Google Earth Engine และ Export เป็น HTML แชร์ได้เลย

### 2. การเปลี่ยน Basemap
Leafmap มี Basemap ให้เลือกมากกว่า 100+ แบบ เช่น:

| Basemap | ลักษณะ | เหมาะกับ |
|---------|--------|----------|
| OpenStreetMap | แผนที่ถนนทั่วไป | งานทั่วไป |
| Esri.WorldImagery | ภาพถ่ายดาวเทียม | Remote Sensing |
| OpenTopoMap | แผนที่ภูมิประเทศ | เห็นเส้นชั้นความสูง |
| CartoDB.DarkMatter | พื้นหลังสีเข้ม | ข้อมูลจุด/Heatmap |

### 3. Marker & Popup
เพิ่มจุดบนแผนที่พร้อมข้อมูลที่แสดงเมื่อคลิก ใช้ `add_marker()` ระบุ `location=[lat, lng]` และ `popup` สำหรับข้อความ

### 4. แสดงข้อมูล GeoJSON
รูปแบบข้อมูลเชิงภูมิศาสตร์บนเว็บ รองรับ Point, Line, Polygon

| รูปแบบไฟล์ | นามสกุล | ฟังก์ชัน |
|------------|---------|----------|
| GeoJSON | .geojson, .json | `add_geojson()` |
| Shapefile | .shp (+ .dbf, .shx) | `add_shp()` |
| GeoTIFF | .tif | `add_raster()` |
| CSV (พิกัด) | .csv | `add_points_from_xy()` |

### 5. แผนที่จาก CSV
มีข้อมูล lat, lng ใน CSV สามารถแสดงบนแผนที่ได้เลยด้วย `add_points_from_xy()`

### 6. Heatmap
แสดงความหนาแน่นหรือค่าของข้อมูลเชิงพื้นที่ด้วย `add_heatmap()` กำหนด radius, blur, max_val

### 7. Split Map
เปรียบเทียบ 2 Basemap พร้อมกัน ลากตรงกลางเพื่อเปลี่ยนด้วย `split_map()`

### 8. Export เป็น HTML
สร้างแผนที่ → เพิ่มข้อมูล → Export ด้วย `m.to_html("map.html")` เปิดใน Browser ได้เลย แชร์ทาง Email/LINE หรือฝังในเว็บไซต์

---

## 📝 แบบฝึกหัด

1. สร้างแผนที่สถานที่ท่องเที่ยว 5 แห่งที่ชอบ พร้อม Marker + Popup
2. สร้าง DataFrame จังหวัดที่เคยไป พร้อมคะแนนความชอบ แสดงบนแผนที่
3. สร้าง Split Map เปรียบเทียบ 2 Basemap ในพื้นที่ที่สนใจ
4. โหลด GeoJSON ของประเทศไทย แสดงบนแผนที่ + Export เป็น HTML

---

## 📂 ไฟล์ในโฟลเดอร์นี้

| ไฟล์ | รายละเอียด |
|------|-----------|
| `Week10_Leafmap_Lecture.pptx` | สไลด์บรรยาย |
| `Week10_Leafmap_InteractiveMap.ipynb` | Notebook Workshop |
| `README.md` | ไฟล์นี้ |

---

## 🔗 สัปดาห์ถัดไป
**Week 11:** Google Earth Engine ด้วย GEEmap — ข้อมูลดาวเทียม, ภาพถ่าย Landsat & Sentinel, NDVI, Time Series

---

*ภาควิชาภูมิศาสตร์ คณะศิลปศาสตร์ มหาวิทยาลัยธรรมศาสตร์*
