# 🏔️ สัปดาห์ที่ 12: การสร้างแผนที่ 3 มิติด้วย MapLibre

## วิชา GE 234 Basic Programming for Geographers

| | |
|---|---|
| **วันที่** | 23 มีนาคม 2569 |
| **สถานะ** | ⏳ ยังไม่สอน |
| **หัวข้อ** | 3D Web Map with WebGL |
| **งานส่ง** | 📋 Code Repository #4 (ส่งก่อนสัปดาห์หน้า) |

---

## 📖 เนื้อหาที่เรียน

### 1. MapLibre คืออะไร?

| | 2D Map (Leafmap) | 3D Map (MapLibre) |
|---|---|---|
| **มุมมอง** | มองจากข้างบน (Top-down) | มองได้ทุกมุม (pitch + bearing) |
| **Tiles** | Raster tiles | Vector tiles + WebGL |
| **3D** | ไม่รองรับ | Extrude อาคาร/ข้อมูลเป็น 3D |

**พารามิเตอร์สำคัญของ 3D Map:**

| พารามิเตอร์ | ความหมาย | ช่วงค่า |
|-------------|----------|---------|
| `pitch` | มุมเอียง (0° = มองตรง, 60° = เอียง) | 0°—85° |
| `bearing` | มุมหมุน/ทิศที่หันไป | -180°—180° |
| `zoom` | ระดับซูม (ยิ่งมาก ยิ่งใกล้) | 0—22 |
| `center` | จุดกึ่งกลาง [lng, lat] | พิกัด |

### 2. 3D Terrain
แสดงภูมิประเทศ 3 มิติจาก DEM ด้วย `add_terrain(exaggeration=2.0)` เพื่อขยายความสูงให้เห็นชัดขึ้น

### 3. 3D Buildings
แสดงอาคารเป็น 3 มิติจากข้อมูล OpenStreetMap ด้วย `add_3d_buildings()` กำหนดสี ความโปร่งใส

### 4. 3D Choropleth Map
ยิ่งค่ามาก = ยิ่งสูง — เข้าใจข้อมูลได้ทันที! ใช้ `fill-extrusion-height` กำหนดความสูงตามค่าข้อมูล เช่น ประชากร, GDP

### 5. Marker & Popup บน 3D Map

> ⚠️ **ข้อควรระวัง:** Leafmap ใช้ `[lat, lng]` แต่ MapLibre ใช้ `[lng, lat]` — สลับกัน! ระวังให้ดี

ใช้ `add_marker(lng_lat=[lon, lat], popup="ข้อความ")`

### 6. Export แผนที่ 3D
สร้าง 3D Map → เพิ่ม Terrain, Buildings, Markers → Export ด้วย `m.to_html("3d_map.html")` — HTML ไฟล์เดียว รวม 3D Map + Terrain + Data เปิดได้ทุก Browser ที่รองรับ WebGL

---

## 📝 แบบฝึกหัด

1. สร้าง 3D Terrain ของภาคเหนือ ปรับ pitch + bearing ให้สวย
2. สร้าง 3D Buildings ของ ม.ธรรมศาสตร์ ปรับสีอาคาร
3. สร้าง 3D Choropleth จากข้อมูลจังหวัดที่สนใจ
4. ผสม Terrain + Markers สถานที่สำคัญ แล้ว Export เป็น HTML

---

## 📂 ไฟล์ในโฟลเดอร์นี้

| ไฟล์ | รายละเอียด |
|------|-----------|
| `Week12_3D_MapLibre_Lecture.pptx` | สไลด์บรรยาย |
| `Week12_3D_MapLibre.ipynb` | Notebook Workshop |
| `README.md` | ไฟล์นี้ |

---

## 🔗 สัปดาห์ถัดไป
**Week 13:** โครงการสุดท้าย (Final Project) — นำเสนอแนวคิดโครงการ, เริ่มพัฒนา, นำเสนอผลงาน

---

*ภาควิชาภูมิศาสตร์ คณะศิลปศาสตร์ มหาวิทยาลัยธรรมศาสตร์*
