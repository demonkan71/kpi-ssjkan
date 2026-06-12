# KPI Dashboard · สสจ.กาญจนบุรี
### ปีงบประมาณ 2569 | เขตสุขภาพที่ 5

---

## 📋 คุณสมบัติ
| ฟีเจอร์ | รายละเอียด |
|---------|------------|
| **ภาพรวม Dashboard** | จำนวนผ่าน/ไม่ผ่าน, คะแนนเฉลี่ย, เปอร์เซ็นต์ความก้าวหน้า |
| **กราฟวิเคราะห์** | รายยุทธศาสตร์, ภาพรวม doughnut chart, Radar chart, District ranking |
| **ผ่านเกณฑ์ / ไม่ผ่านเกณฑ์** | แยกรายการ พร้อม pagination หน้าละ 15 รายการ |
| **ตัวชี้วัดทั้งหมด** | แสดงรายเดือน/รายไตรมาส, กรองตามยุทธศาสตร์, สถานะ |
| **ข้อมูลรายอำเภอ** | 13 อำเภอ พร้อมคะแนนเฉลี่ยและ filter |
| **รายไตรมาส** | Q1-Q4 พร้อมปุ่มเปลี่ยนไตรมาส |
| **บันทึกข้อมูล** | ฟอร์มบันทึกข้อมูลตัวชี้วัด ประวัติการบันทึก |
| **ส่งออก Excel** | ส่งออกไฟล์ .xlsx พร้อมชีตรายอำเภอ |
| **ส่งออก PDF** | ส่งออกรายงาน PDF |
| **ฐานข้อมูล** | localStorage (ค่าเริ่มต้น) + Google Sheets (ออนไลน์ฟรี) |

---

## 🚀 วิธีใช้งาน

### วิธีที่ 1: เปิดไฟล์ตรงๆ (ง่ายที่สุด)
1. เปิดโฟลเดอร์ `ssj_kan_dashboard`
2. ดับเบิลคลิก `index.html`
3. เปิดใน Chrome / Edge / Firefox
4. **ทั้งหมดออฟไลน์ได้** — ข้อมูลถูกฝังในไฟล์แล้ว

### วิธีที่ 2: ใช้ Web Server (แนะนำ)
```bash
# ถ้ามี Python
cd ssj_kan_dashboard
python -m http.server 8080

# แล้วเปิด http://localhost:8080
```

### วิธีที่ 3: Deploy ขึ้นออนไลน์ (ฟรี)
- **Vercel:** `vercel --prod` (ฟรี)
- **Netlify:** ลากโฟลเดอร์ไปวาง
- **GitHub Pages:** push ไป repo แล้วเปิด GitHub Pages

---

## 🗄️ เชื่อมต่อ Google Sheets (ฐานข้อมูลออนไลน์ฟรี)

### ขั้นตอน
1. เปิด https://script.google.com/ → สร้างโปรเจกต์ใหม่
2. คัดลอกเนื้อหาจาก `google_apps_script.gs` วางทั้งหมด
3. สร้าง Google Sheet ชื่อ "SSJ_Kan_DB"
   - หัว columns: timestamp, kpi_id, kpi_name, strategy, target, actual, pass_fail, quarter, district, note
4. แก้ไข `SHEET_ID` ใน Apps Script ให้เป็น ID ของ Sheet (ดูได้จาก URL)
5. Deploy → New deployment → Web app
   - Execute as: Me
   - Access: Anyone
6. คัดลอก Web App URL
7. เปิด Dashboard → ตั้งค่า → ใส่ URL → ทดสอบเชื่อมต่อ

---

## 📁 โครงสร้างไฟล์
```
ssj_kan_dashboard/
├── index.html              # Dashboard หลัก (เปิดใน browser ได้เลย)
├── google_apps_script.gs   # Backend สำหรับ Google Sheets
└── README.md               # คู่มือนี้
```

---

## 🎨 รายละเอียดเทคนิค
- **UI Framework:** Bootstrap 5.3 (dark theme)
- **Charts:** Chart.js 4
- **Alerts:** SweetAlert2 11
- **Icons:** Font Awesome 6
- **Export Excel:** SheetJS (xlsx)
- **Export PDF:** html2canvas + jsPDF
- **Storage:** localStorage (default) + Google Sheets REST API
- **Responsive:** Mobile + Desktop
- **Print-friendly:** CSS @media print

---

## 📊 ข้อมูล KPI ที่บรรจุแล้ว
- **จำนวน KPI:** 42 ตัวชี้วัด
- **ยุทธศาสตร์:** 5 ยุทธศาสตร์
- **อำเภอ:** 13 อำเภอ
- **รอบข้อมูล:** Q1-Q4 ปีงบ 2569

---

## 🤝 การปรับแต่งเพิ่มเติม
- เพิ่ม KPI: แก้ไขอาเรย์ `KPI_DATA` ใน `<script>` ของ `index.html`
- เปลี่ยนสีธีม: แก้ไข CSS variables ใน `:root`
- เพิ่ม district data: เพิ่มข้อมูลในออบเจ็กต์ `DISTRICT_DATA`
- ปรับจำนวนต่อหน้า: เปลี่ยน `PAGE_SIZE` (ค่าเริ่มต้น 15)

---

พัฒนาโดย ❤️ สำหรับ สสจ.กาญจนบุรี  
Hermes Agent · Nous Research
"#kpi-ssjkan" 
