---
title: แอปติดตั้งได้ (PWA)
---

[← หน้าแรก](../index.md)

# แอปติดตั้งได้ (PWA)

แอปใหม่ที่สร้างใน KODRA (เทมเพลตเริ่มต้น React + Vite) เป็น **PWA (Progressive Web App) ตั้งแต่แรก**
หลังเผยแพร่แล้ว ผู้ใช้กด **เพิ่มไปยังหน้าจอโฮม** / **ติดตั้งแอป** จากเบราว์เซอร์ได้ แอปจะเปิดเต็มจอเหมือนแอปมือถือ
ไม่ต้องตั้งค่าอะไรเพิ่ม และไม่ต้องติดตั้งแพ็กเกจเพิ่ม

แอปที่สร้างก่อนหน้านี้ไม่ถูกเปลี่ยน

## ได้อะไรบ้าง

- **ติดตั้งได้** — ไฟล์ manifest สร้างตอน build: ชื่อแอปมาจาก `<title>` ใน `index.html`
  (ชื่อบนหน้าจอโฮมย่อเหลือไม่เกิน 12 ตัวอักษร) ไอคอนมาจากโฟลเดอร์ `public/icons/`
- **สีตามแบรนด์** — สีของแถบด้านบนและหน้าจอตอนเปิดแอปมาจากสีหลักและสีพื้นหลังที่ตั้งไว้ใน
  [Brand Studio](brand-and-design.md) (design tokens ใน `src/globals.css`) เปลี่ยนสีในแท็บ **แบรนด์**
  แล้ว build ใหม่ สีของ PWA ก็เปลี่ยนตาม
- **หน้าออฟไลน์** — ถ้าผู้ใช้ไม่มีอินเทอร์เน็ต จะเห็นหน้า "ไม่ได้เชื่อมต่ออินเทอร์เน็ต / You're offline"
  (ภาษาไทยและอังกฤษ) พร้อมปุ่ม **ลองอีกครั้ง · Try again** และโหลดใหม่เองเมื่อกลับมาออนไลน์
- **แจ้งเมื่อมีเวอร์ชันใหม่** — เมื่อคุณเผยแพร่เวอร์ชันใหม่ ผู้ใช้ที่เปิดแอปอยู่จะเห็นข้อความ
  **มีเวอร์ชันใหม่** พร้อมปุ่ม **โหลดใหม่** (เป็นภาษาอังกฤษ "New version available" / "Reload"
  ถ้าหน้าเว็บไม่ได้ตั้งภาษาเป็นไทย) — แอปไม่โหลดใหม่เองจนกว่าผู้ใช้จะกด

## ปลอดภัยกับข้อมูล

- **ไม่แคช `/api`** ของแอป และไม่แตะคำขอไปเว็บอื่น (API ภายนอก, ระบบล็อกอิน, การชำระเงิน)
- **ไม่แคชหน้าเว็บ** — หน้าโหลดจากเครือข่ายทุกครั้ง ผู้ใช้จึงไม่เห็นข้อมูลเก่า แคชเฉพาะไฟล์ JavaScript/CSS
  ที่ build แล้ว (ชื่อไฟล์เปลี่ยนทุกเวอร์ชัน) และหน้าออฟไลน์
- **ไม่ทำงานในพรีวิวของ KODRA** — PWA ทำงานเฉพาะเวอร์ชันที่ build จริง (เผยแพร่แล้ว) ในพรีวิวจึงไม่เห็น
  ปุ่มติดตั้งหรือหน้าออฟไลน์ เป็นเรื่องปกติ

## เปลี่ยนไอคอน

แทนไฟล์ใน `public/icons/` ด้วยโลโก้ของคุณ **ใช้ชื่อไฟล์และขนาดเดิม**:

| ไฟล์ | ขนาด |
|---|---|
| `icon-192.png` | 192×192 |
| `icon-512.png` | 512×512 |
| `icon-maskable-512.png` | 512×512 (เว้นขอบให้โลโก้อยู่กลาง เพราะระบบอาจตัดเป็นวงกลม) |
| `apple-touch-icon.png` | 180×180 (สำหรับ iPhone/iPad) |
| `icon.svg` | ไอคอนแบบเวกเตอร์ |

หรือแนบรูปโลโก้แล้วบอก AI ในแชตว่า *"เปลี่ยนไอคอนแอปเป็นโลโก้นี้"*

## ปิด PWA

ถ้าไม่อยากให้แอปติดตั้งได้ แก้ `vite.config.ts` จาก `pwa({ enabled: true })` เป็น:

```ts
pwa({ enabled: false }),
```

หรือบอก AI ว่า *"ปิด PWA"* แล้วเผยแพร่ใหม่ — เวอร์ชันถัดไปจะไม่มี manifest และจะลบ service worker
เดิมออกจากเครื่องของผู้ใช้ที่เคยเปิดแอปไว้ให้เอง

---

## English

New apps (the default React + Vite template) are **installable PWAs** out of the
box, with no extra packages:

- The manifest is generated at build time: name from the `<title>` in
  `index.html`, icons from `public/icons/`, theme/background colors from your
  [Brand Studio](brand-and-design.md) design tokens.
- **Offline page** in Thai and English ("You're offline", **Try again**).
- **Update toast:** "New version available" / **Reload** (Thai when the page is
  in Thai); it never reloads on its own.
- **Never caches `/api`** or other origins; pages are always loaded from the
  network (no stale data); only hashed build assets and the offline page are
  cached.
- **Not active in the KODRA preview** — only in production builds.
- **Icons:** replace the files in `public/icons/` keeping the same names and
  sizes.
- **Turn it off:** `pwa({ enabled: false })` in `vite.config.ts`, then publish
  again; the next version also removes the old service worker from visitors'
  devices.

Existing apps are not changed.
