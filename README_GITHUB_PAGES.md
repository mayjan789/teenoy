# ระบบสร้างคอนเทนต์และภาพสำหรับขายสินค้า - GitHub Pages Edition

ระบบเว็บแอปพลิเคชันสำหรับสร้างคอนเทนต์การตลาดและภาพสินค้าที่ครบวงจร ที่ปรับแต่งให้ทำงานได้บน GitHub Pages

## ฟีเจอร์หลัก

### 1. หน้าหลัก - จัดการข้อมูลสินค้า
- กรอกข้อมูลสินค้า (ชื่อ, รายละเอียด, ราคา, คุณสมบัติ)
- อัปโหลดรูปอ้างอิงสินค้า (หลายรูป)
- เลือกฉากและสไตล์
- เลือกโมเดล (นางแบบ/นายแบบ/คู่)
- เลือกโทนสี
- ข้อมูลเก็บไว้ใน localStorage

### 2. เมนูสร้างคอนเทนต์
- **Facebook Captions**: สร้างคำบรรยายสำหรับ Facebook
- **TikTok Captions**: สร้างคำบรรยายสำหรับ TikTok
- **Shopee Captions**: สร้างคำบรรยายสำหรับ Shopee

### 3. เมนูสร้างภาพและเสียง
- **Image-to-Image**: สร้างภาพใหม่จากรูปอ้างอิง
- **Voice Scripts**: สร้างสคริปต์เสียง
- **AI Video Prompts**: สร้าง prompt สำหรับวิดีโอ AI

## การติดตั้งและใช้งาน

### ติดตั้ง Dependencies
```bash
npm install
```

### รันโปรเจกต์ในเครื่อง
```bash
npm run dev
```

### Build สำหรับ Production
```bash
npm run build
```

### Preview Build
```bash
npm run preview
```

## การ Deploy ไปยัง GitHub Pages

### 1. สร้าง GitHub Repository
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git
git push -u origin main
```

### 2. ตั้งค่า GitHub Pages
1. ไปที่ Settings ของ Repository
2. ไปที่ Pages
3. เลือก Deploy from a branch
4. เลือก `main` branch และ `/ (root)` folder
5. Save

### 3. GitHub Actions จะทำการ Deploy อัตโนมัติ
- เมื่อ push ไปยัง main branch
- GitHub Actions จะ build และ deploy ไปยัง GitHub Pages
- ตรวจสอบ Actions tab เพื่อดูสถานะ

## โครงสร้างโปรเจกต์

```
content-generator/
├── client/
│   ├── src/
│   │   ├── pages/           # React pages
│   │   ├── components/      # Reusable components
│   │   ├── hooks/           # Custom hooks
│   │   ├── lib/             # Utilities
│   │   ├── App.tsx          # Main app component
│   │   ├── main.tsx         # Entry point
│   │   └── index.css        # Global styles
│   ├── public/              # Static assets
│   └── index.html           # HTML template
├── shared/                  # Shared types and constants
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Actions workflow
├── vite.config.ts           # Vite configuration
└── package.json             # Dependencies
```

## การจัดเก็บข้อมูล

ข้อมูลสินค้าจะถูกจัดเก็บใน **localStorage** ของเบราว์เซอร์ ซึ่งหมายความว่า:
- ข้อมูลจะยังคงอยู่แม้ปิดเบราว์เซอร์
- ข้อมูลเป็นแบบ local ต่อเบราว์เซอร์แต่ละตัว
- สามารถ export/import ข้อมูลได้ถ้าต้องการ

## การปรับแต่ง

### เปลี่ยน Repository Name
หากชื่อ repository ไม่ใช่ `content-generator` ให้อัปเดตใน:
1. `vite.config.ts` - ตั้ง `VITE_REPO_NAME`
2. `.github/workflows/deploy.yml` - จะอัปเดตอัตโนมัติ

### เปลี่ยนสี Theme
แก้ไขไฟล์ `client/src/index.css` เพื่อเปลี่ยนสีของแอปพลิเคชัน

### เพิ่มฟีเจอร์เพิ่มเติม
1. สร้างไฟล์ component ใหม่ใน `client/src/components/`
2. สร้างไฟล์ page ใหม่ใน `client/src/pages/`
3. เพิ่ม route ใน `client/src/App.tsx`

## ข้อจำกัด

- ไม่มี backend/database - ข้อมูลเก็บใน localStorage เท่านั้น
- ไม่มี authentication - ทุกคนสามารถเข้าถึงข้อมูลได้
- ไม่สามารถ upload ไฟล์ไปยัง server ได้ - เฉพาะ base64 เท่านั้น

## การพัฒนาเพิ่มเติม

หากต้องการเพิ่มฟีเจอร์ backend:
1. สร้าง API server (Node.js, Python, etc.)
2. เพิ่ม environment variables สำหรับ API URL
3. แก้ไข hooks เพื่อเรียก API แทน localStorage

## Support

สำหรับปัญหาหรือคำถาม:
1. ตรวจสอบ GitHub Issues
2. สร้าง Issue ใหม่พร้อมรายละเอียด
3. ส่ง Pull Request หากมีการปรับปรุง

## License

MIT License - ใช้งานได้อย่างอิสระ
