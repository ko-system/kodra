---
title: เชื่อมต่อ Neon
---

[← หน้าแรก](../index.md)

# เชื่อมต่อ Neon (Postgres)

[Neon](https://neon.tech) คือฐานข้อมูล Postgres แบบ serverless ที่แยก branch ได้
ใช้ได้กับแอป **Next.js** และ **Vite**

## ขั้นตอน

1. ในแอปที่ต้องการ กดเชื่อมต่อ Neon จะเปิดหน้าต่างเชื่อมต่อ
2. เปิดหน้า API keys ของ Neon: <https://console.neon.tech/app/settings/api-keys>
3. ในส่วน **Personal API keys** กด **Create new API key** ตั้งชื่อ เช่น `KODRA`
4. คัดลอก key (ขึ้นต้นด้วย `napi_`) มาวางในช่อง **Personal API key** แล้วกด **Connect**

> ต้องเป็น **Personal** API key — key แบบ organization หรือ project ดูรายการโปรเจกต์ไม่ได้

KODRA ใช้ key นี้เพื่อดู/สร้างโปรเจกต์และ branch และอ่าน connection string
ยกเลิก key ได้ที่หน้าเดียวกัน การกด Disconnect ใน KODRA จะลบ key ที่บันทึกไว้

## หลังเชื่อมต่อ

- KODRA เขียน `DATABASE_URL` ลงไฟล์ `.env.local` ของแอปให้
- branch ของฐานข้อมูลมีป้าย Production / Development / Preview / Snapshot
- **Migrate to Production** — คัดลอก schema ไปยัง production โดยให้คุณตรวจ SQL ก่อน
- **Require email verification** — เปิดการยืนยันอีเมลของ Neon Auth
- **Sync to Vercel** — ส่ง environment variables ไปยัง Vercel

แอปหนึ่งใช้ Neon หรือ [Supabase](supabase.md) ได้อย่างใดอย่างหนึ่งเท่านั้น
เทมเพลต [Portal](../templates/portal.md) ต้องใช้ Neon

---

## English

Neon is serverless Postgres with branching (Next.js and Vite apps). Open
<https://console.neon.tech/app/settings/api-keys> → **Personal API keys** →
**Create new API key** (name it "KODRA") → paste the `napi_…` key into **Personal
API key** → **Connect**. It must be a *personal* key; organization or project
keys can't list projects. KODRA uses it to list/create projects and branches and
read connection strings, writes `DATABASE_URL` to `.env.local`, and offers
**Migrate to Production** (review the SQL first), **Require email verification**
and **Sync to Vercel**. Disconnecting forgets the key. One database integration
per app; the Portal template requires Neon.
