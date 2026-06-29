# WP Article AI — ระบบสร้างบทความ SEO

สร้างบทความภาษาไทย SEO อัตโนมัติด้วย Claude AI และโพสไป WordPress หลายเว็บพร้อมกัน

## โครงสร้างไฟล์

```
wp-article-generator/
├── index.html        ← หน้าเว็บหลัก (frontend)
├── api/
│   └── chat.js       ← Vercel Serverless Function (ซ่อน API Key)
├── vercel.json       ← Vercel configuration
└── README.md
```

## วิธี Deploy บน Vercel

### 1. อัปโหลดขึ้น GitHub
- สร้าง repo ใหม่บน github.com
- อัปโหลดไฟล์ทั้งหมด (ทั้ง 4 ไฟล์)

### 2. Deploy บน Vercel
- ไปที่ vercel.com → Import GitHub repo
- กด Deploy

### 3. ตั้งค่า API Key (สำคัญมาก)
- Vercel Dashboard → Project → Settings → Environment Variables
- เพิ่ม: `ANTHROPIC_API_KEY` = `sk-ant-api03-...`
- กด Save → Redeploy

## แก้ปัญหา CORS ของ WordPress

เพิ่มใน `.htaccess` ของ WordPress:

```apache
Header set Access-Control-Allow-Origin "*"
Header set Access-Control-Allow-Methods "GET, POST, OPTIONS, PUT"
Header set Access-Control-Allow-Headers "Authorization, Content-Type"
```

หรือติดตั้ง Plugin: **WP CORS** (ค้นหาใน WordPress Plugin Directory)

## การใช้งาน

1. ไปที่ **เว็บไซต์** → เพิ่ม WordPress URL + Username + App Password
2. ไปที่ **สร้างบทความ** → กรอกหัวข้อ + keyword
3. เลือกเว็บที่จะโพส → กด **สร้างบทความ + โพส**
4. ดูรายงานใน **สรุปรายงาน** และ Export Excel ได้

## รับ Claude API Key

1. ไปที่ console.anthropic.com
2. สมัครสมาชิก/Login
3. API Keys → Create Key
4. คัดลอก key ที่ขึ้นต้น `sk-ant-api03-...`
