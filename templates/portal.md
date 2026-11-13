---
title: เทมเพลต Portal
---

[← หน้าแรก](../index.md)

# เทมเพลต Portal: Mini Store

**Portal: Mini Store Template** เป็นเทมเพลตร้านค้าขนาดเล็กที่ใช้ **Next.js**, **Payload CMS**
(ระบบหลังบ้านจัดการเนื้อหา) และฐานข้อมูล **Neon** (Postgres) — ยังเป็นเทมเพลตทดลอง
ซอร์สโค้ด: [ko-system/portal-mini-store-template](https://github.com/ko-system/portal-mini-store-template)

## เริ่มใช้งาน

1. [เชื่อมต่อ Neon](../integrations/neon.md) ก่อน (ถ้ายังไม่เชื่อม จะเห็น
   "Please connect your Neon account to use this template.")
2. ไปที่หน้า **Templates** แล้วเลือก Portal เป็นเทมเพลตเริ่มต้น
3. สร้างแอปใหม่จากหน้าแรกตามปกติ

## สร้าง database migration {#create-a-database-migration}

ทุกครั้งที่แก้ collection หรือ field ใน Payload (โครงสร้างข้อมูล) ต้องสร้างไฟล์ migration
เพื่อให้ฐานข้อมูล production เปลี่ยนตาม

1. เปิดแท็บ **Publish** จะมีการ์ด **Portal Database Migration**
   (แสดงเมื่อแอปมีโปรเจกต์ Neon และไฟล์ `payload.config.ts`)
2. กด **Generate database migration**
   KODRA จะรัน `npm run migrate:create -- --skip-empty` แล้ว commit ไฟล์ migration ให้
   ผลลัพธ์แสดงใน **Command Output**
3. สำเร็จจะเห็น "Database migration file generated and committed successfully!"

ทำเองใน terminal ที่โฟลเดอร์แอปได้:

```sh
npm run migrate:create -- --skip-empty
git add -A && git commit -m "Generate database migration"
```

| ข้อความ | ความหมาย |
|---|---|
| "No migration was created because no changes were found." | โครงสร้างข้อมูลไม่เปลี่ยน ไม่ต้องทำอะไร |
| "Migration creation failed (exit code N)…" | ดู Command Output — มักเป็น error ใน config ของ Payload ให้ส่ง error ให้ AI แก้ |
| หมดเวลา (timeout) | ลองใหม่ หรือรันคำสั่งเองใน terminal |

ถ้าแอปใช้ branch ของ Neon จะเห็นส่วน Database พร้อมปุ่ม **Migrate to Production** แทนการ์ดนี้
ดู [Neon](../integrations/neon.md)

---

## English

**Portal: Mini Store Template** (experimental) uses Next.js, Payload CMS and Neon
Postgres; source at
[ko-system/portal-mini-store-template](https://github.com/ko-system/portal-mini-store-template).
Connect [Neon](../integrations/neon.md) first, pick Portal on the **Templates**
page, then create an app.

**Create a database migration** whenever you change Payload collections/fields:
**Publish** tab → **Portal Database Migration** → **Generate database
migration**. KODRA runs `npm run migrate:create -- --skip-empty` and commits the
file (or run it yourself and commit). "No migration was created because no
changes were found" means there was nothing to do; on failure read the Command
Output and ask the AI to fix the Payload config. Apps on Neon branches use
**Migrate to Production** instead.
