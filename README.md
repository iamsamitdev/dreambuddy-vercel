# DreamBuddy (เพื่อนล่าฝัน) 🎯💰

DreamBuddy คือเว็บแอปพลิเคชันสำหรับตั้งเป้าหมายการออมเงินและติดตามความคืบหน้า พร้อมฟีเจอร์โซเชียลที่ช่วยให้คุณและเพื่อนๆ สามารถให้กำลังใจกันในการไปถึงฝั่งฝัน

## ✨ ฟีเจอร์หลัก

*   **Goal Tracking:** สร้างและจัดการเป้าหมายการออมเงิน (เช่น เที่ยว, ซื้อของ, การศึกษา)
*   **Transactions:** บันทึกรายการฝาก/ถอนเงินในแต่ละเป้าหมาย
*   **Social Features:**
    *   แชร์เป้าหมายแบบ Public หรือ Link-only
    *   กด Like ให้กำลังใจเป้าหมายของเพื่อน
    *   คอมเมนต์พูดคุยในแต่ละเป้าหมาย
*   **Authentication:** ระบบสมาชิก (Login/Register) พร้อมรองรับ Social Login (Google, GitHub)
*   **Multi-language:** รองรับหลายภาษา (ไทย, อังกฤษ, ญี่ปุ่น, ลาว)

## 🛠️ เทคโนโลยีที่ใช้ (Tech Stack)

*   **Framework:** [Nuxt 4](https://nuxt.com) (Vue.js Framework)
*   **Language:** TypeScript
*   **Database:** PostgreSQL
*   **ORM:** [Prisma](https://www.prisma.io)
*   **UI Library:** [Nuxt UI](https://ui.nuxt.com) & [Tailwind CSS](https://tailwindcss.com)
*   **Authentication:** Custom JWT Auth (Cookies)
*   **Deployment:** Vercel

## 🚀 การติดตั้งและเริ่มต้นใช้งาน (Setup)

โปรเจ็กต์นี้ใช้ [Bun](https://bun.sh) ในการจัดการแพ็กเกจ

### 1. Clone โปรเจ็กต์

```bash
git clone https://github.com/iamsamitdev/dreambuddy-vercel.git
cd dreambuddy-vercel
```

### 2. ติดตั้ง Dependencies

```bash
bun install
```

### 3. ตั้งค่า Environment Variables

สร้างไฟล์ `.env` ที่ root ของโปรเจ็กต์ และกำหนดค่าดังนี้:

```env
# การเชื่อมต่อฐานข้อมูล PostgreSQL
DATABASE_URL="postgresql://user:password@localhost:5432/dreambuddy?schema=public"

# Secret Key สำหรับ JWT (ควรเป็นสตริงยาวๆ ที่เดายาก)
JWT_SECRET="your-super-secret-jwt-key-change-this"

# อายุของ Token (เช่น 7d, 24h)
JWT_EXPIRES_IN="7d"
```

### 4. ตั้งค่าฐานข้อมูล (Prisma)

สร้างตารางในฐานข้อมูลและสร้าง Prisma Client:

```bash
# สร้างตารางใน DB ตาม schema.prisma
bun x prisma db push

# (ทางเลือก) ลงข้อมูลตัวอย่าง
bun x prisma db seed
```

### 5. รันโปรเจ็กต์ (Development)

```bash
bun run dev
```

เปิดเบราว์เซอร์ไปที่ `http://localhost:3000`

## 📂 โครงสร้างโปรเจ็กต์

*   `app/`: โค้ดส่วนหน้า (Frontend) ทั้งหมด
    *   `pages/`: หน้าเว็บ (Routes)
    *   `components/`: Vue Components
    *   `layouts/`: Layouts ของหน้าเว็บ
    *   `middleware/`: Route Middleware (เช่น ตรวจสอบการ Login)
    *   `locales/`: ไฟล์แปลภาษา
*   `server/`: โค้ดส่วนหลัง (Backend API)
    *   `api/`: API Endpoints (เช่น `/api/auth/login`)
    *   `utils/`: Utility functions ฝั่ง Server (เช่น Prisma instance, Auth helpers)
*   `prisma/`: การตั้งค่าฐานข้อมูล
    *   `schema.prisma`: โครงสร้างตารางฐานข้อมูล
    *   `migrations/`: ไฟล์ Migration
    *   `seed.ts`: ข้อมูลตัวอย่าง

## 📦 การ Build สำหรับ Production

```bash
bun run build
```

สามารถดูผลลัพธ์การ Build ได้ด้วยคำสั่ง:

```bash
bun run preview
```

## ☁️ การ Deploy (Vercel)

โปรเจ็กต์นี้ตั้งค่าไว้สำหรับ Deploy บน Vercel โดยเฉพาะ (`preset: 'vercel'`)

1.  ติดตั้ง [Vercel CLI](https://vercel.com/docs/cli) หรือเชื่อมต่อ GitHub Repository กับ Vercel Dashboard
2.  ตั้งค่า Environment Variables ใน Vercel Project Settings (`DATABASE_URL`, `JWT_SECRET`, ฯลฯ)
3.  Deploy!

---

พัฒนาด้วย ❤️ โดย [iamsamitdev]
