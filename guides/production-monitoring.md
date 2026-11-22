---
title: ข้อผิดพลาดบนเว็บจริง และสถานะเว็บไซต์จริง
---

[← หน้าแรก](../index.md)

# ข้อผิดพลาดบนเว็บจริง และสถานะเว็บไซต์จริง

หลังเผยแพร่แล้ว KODRA ช่วยเฝ้าเว็บจริงต่อได้ 2 แบบ ทั้งคู่อยู่ในแท็บ **เผยแพร่** (Publish) ของแผง Preview:

- **ข้อผิดพลาดบนเว็บจริง** (Production errors) — ข้อผิดพลาดที่ผู้เข้าชมจริงเจอ จัดกลุ่มตามสาเหตุ
  แล้วกด **ให้ AI แก้** ได้ในคลิกเดียว (ต้องเปิดเอง)
- **สถานะเว็บไซต์จริง** (Live site health) — ตรวจว่าเว็บยังเปิดได้ และแจ้งเตือนเมื่อสิ่งที่เคยใช้ได้เกิดพัง

ไม่มีบริการภายนอก (third-party) เกี่ยวข้อง ข้อมูลส่งมาที่ KODRA เท่านั้น

## ข้อผิดพลาดบนเว็บจริง

### เปิดใช้งาน

เปิดสวิตช์ **รายงานข้อผิดพลาด** (Error reporting) ในการ์ด **ข้อผิดพลาดบนเว็บจริง** — ปิดไว้เป็นค่าเริ่มต้น
และเปิดแยกทีละแอป ไม่ต้อง build ใหม่ ไม่มีการแก้โค้ดของแอป: เซิร์ฟเวอร์ที่โฮสต์เว็บจะแทรกสคริปต์เล็ก ๆ
(`/__kodra/reporter.js`) ให้เอง

- **ใช้ได้กับเว็บที่โฮสต์บน KODRA** (เวอร์ชันเว็บ เผยแพร่ที่ `ชื่อของคุณ.wt.in.th`) — ต้องเผยแพร่แอปไปยัง
  ที่อยู่บน KODRA ก่อน
- **โฮสต์อื่น (Vercel, Cloudflare, Coolify) บนเวอร์ชันเว็บ:** เปิดหัวข้อ **เก็บข้อผิดพลาดจากโฮสต์อื่นด้วย**
  กด **คัดลอก** แล้ววางบรรทัด `<script …>` ที่ได้ลงใน `<head>` ของ `index.html`
  ในเวอร์ชันที่ deploy ไปโฮสต์นั้น
- **ใช้แต่ desktop:** ใช้ได้เฉพาะเว็บที่โฮสต์บน KODRA เท่านั้น เว็บที่ deploy จากเครื่องไป Vercel, Cloudflare
  หรือ Coolify ไม่มีปลายทางให้ส่งข้อผิดพลาด

### เก็บอะไรบ้าง และอะไรถูกลบออก

สิ่งที่เก็บ:

- ชนิดข้อผิดพลาด: **ข้อผิดพลาด** (JavaScript error), **Promise ที่ไม่ได้จัดการ**, **เรียก API ไม่สำเร็จ**
  (คำขอไป `/api/…` ของเว็บเองที่ตอบ 5xx) และ **เซิร์ฟเวอร์ผิดพลาด** (แอปที่มีเซิร์ฟเวอร์ตอบ 5xx —
  เก็บแค่ method และ path)
- ข้อความ error และ stack, **หน้า** ที่เกิด (เหลือแค่รูปแบบของ path เช่น `/orders/:id`),
  ชื่อ **เบราว์เซอร์** (เช่น Chrome, Safari), เวลา, จำนวนครั้ง และเวอร์ชัน (release) ที่เกิด

สิ่งที่ **ถูกลบออกตั้งแต่ในเบราว์เซอร์ และลบซ้ำอีกครั้งที่เซิร์ฟเวอร์**: อีเมล เบอร์โทร
เลขบัตร/เลขประจำตัวประชาชน โทเคนและรหัสลับ query string (ส่วนหลัง `?`) และค่าใน URL ที่เป็นโทเคน
**ไม่เก็บ** คุกกี้ ค่าที่กรอกในฟอร์ม และ IP address

มีการจำกัดอัตรา (rate limit) ต่อเว็บและต่อผู้เข้าชม รายงานที่เกินจะถูกทิ้ง และการ์ดจะบอกจำนวนที่ทิ้งไป

### ใช้งานรายการข้อผิดพลาด

- ข้อผิดพลาดที่มาจากสาเหตุเดียวกันถูก **จัดกลุ่ม** แสดงจำนวนครั้ง ครั้งแรก/ล่าสุด หน้า และเบราว์เซอร์
  กด **ดูรายละเอียด** เพื่อดู stack
- **ให้ AI แก้** — ส่งรายละเอียดกลุ่มนั้นเข้าแชตของแอป (ต้องเปิดแชตของแอปไว้ก่อน)
  ในโหมด Agent AI ยังอ่านรายการข้อผิดพลาดบนเว็บจริงเองได้ด้วย
- **ไม่สนใจ** — ซ่อนกลุ่มนั้น แต่ **ถ้าเกิดอีกในเวอร์ชันที่เผยแพร่ใหม่กว่า จะกลับมาแสดง**

### ตำแหน่งในโค้ด (source map)

ถ้าอยากให้แต่ละกลุ่มบอก **ตำแหน่งในโค้ด** (เช่น `src/pages/Cart.tsx:42:7`) ให้แอป build พร้อม
source map แบบซ่อน ใน `vite.config.ts`:

```ts
export default defineConfig(() => ({
  build: { sourcemap: "hidden" },
  // ...
}));
```

แบบ `"hidden"` จะไม่ผูก source map เข้ากับไฟล์ JavaScript ผู้เข้าชมจึงไม่ถูกชี้ให้ไปโหลดโค้ดต้นฉบับ
หรือบอก AI ในแชตว่า *"เปิด source map แบบ hidden ให้หน่อย"* ก็ได้

## สถานะเว็บไซต์จริง

- **ตรวจเว็บไซต์จริงทุก** 15 / 30 / 60 / 180 นาที (ค่าเริ่มต้น **30 นาที**) — เปิดหน้าแรกและหน้าเริ่มต้น
  ของโฟลว์ที่บันทึกไว้ หน้าละครั้ง กด **ตรวจตอนนี้** เพื่อตรวจทันที
- การ์ดแสดง **ออนไลน์** / **ล่ม**, เวลาตอบสนอง, **ตรวจล่าสุด** และ **มีปัญหาตั้งแต่** เมื่อเว็บล่ม
- **เว็บที่โฮสต์บน KODRA:** เซิร์ฟเวอร์ตรวจให้ (**ตรวจโดยเซิร์ฟเวอร์ KODRA**) แม้ปิด KODRA อยู่
  เปิดเป็นค่าเริ่มต้น
- **โฮสต์อื่น (Vercel, Cloudflare, Coolify):** ตรวจจาก KODRA ของคุณ (**ตรวจจาก KODRA เครื่องนี้**)
  เฉพาะตอนที่เปิด KODRA และบอกอายุที่เหลือของใบรับรอง HTTPS ด้วย

### รันโฟลว์บนเว็บจริง

เปิด **รันโฟลว์ที่ปลอดภัยบนเว็บไซต์จริง** เพื่อเล่นโฟลว์ที่บันทึกไว้ (โฟลว์ถูกบันทึกเมื่อการทดสอบในเบราว์เซอร์
ผ่านในแชต) บนเว็บจริงด้วย ปิดไว้เป็นค่าเริ่มต้น

- รันเฉพาะโฟลว์ที่คุณติ๊ก **ปลอดภัยที่จะรันบนเว็บไซต์จริง**
- **ทำเครื่องหมายได้เฉพาะโฟลว์ที่อ่านอย่างเดียว** — โฟลว์ที่กรอกฟอร์ม ส่งข้อมูล สร้าง บันทึก หรือลบอะไร
  จะขึ้น **มีการแก้ไขข้อมูล — รันบนเว็บจริงไม่ได้** และถูกปฏิเสธอีกครั้งตอนรัน
- โฟลว์ที่ไม่ผ่านมี **ภาพหน้าจอ** หน้าสุดท้ายให้ดู

### การแจ้งเตือน

เมื่อสิ่งที่ **เคยผ่าน** เริ่ม **ไม่ผ่าน** (เว็บล่ม หรือโฟลว์ที่เคยผ่านพัง) KODRA จะขึ้นแถบ
**"<ชื่อแอป>: เว็บไซต์จริงมีปัญหา"** พร้อมปุ่ม **เปิดแอป** (บน desktop มีการแจ้งเตือนของระบบด้วย)
แถบจะหายเมื่อกด **ปิด** หรือเมื่อเว็บกลับมาปกติ

## path ที่สงวนไว้บนเว็บที่เผยแพร่ (`/__kodra/`)

บนเว็บที่โฮสต์บน KODRA path ต่อไปนี้เป็นของ KODRA ไม่ใช่ของแอป:

- `/__kodra/reporter.js` — สคริปต์รายงานข้อผิดพลาด
- `/__kodra/errors` — ปลายทางรับรายงาน

อย่าสร้างหน้าหรือ API ของแอปไว้ใต้ `/__kodra/` (ถ้าเว็บไม่ได้เปิดรายงานข้อผิดพลาด สอง path นี้ตอบ 404)

---

## English

The app's **Publish** tab has two cards for watching the live site:

- **Production errors** — opt-in per app via the **Error reporting** switch.
  Works for KODRA-hosted sites (the web version's `yourname.wt.in.th`); publish
  there first. On the web version you can also collect from Vercel, Cloudflare
  or Coolify by pasting the script tag from **Also collect errors from your
  other hosts** into `index.html`'s `<head>`. Desktop-only users: KODRA-hosted
  sites only. Collected: error kind (JS error, unhandled promise, failed
  `/api` request, server 5xx), message and stack, page route shape, browser
  family, time, count and release. Scrubbed in the browser and again on the
  server: emails, phone numbers, ID/card numbers, tokens and secrets, query
  strings; cookies, form values and IP addresses are never stored. Errors are
  grouped by cause; **Fix with AI** sends a group to the app's open chat;
  **Ignore** hides a group until it happens again in a newer release. For
  source locations build with `build: { sourcemap: "hidden" }`.
- **Live site health** — checks the home page and saved-flow start pages every
  15/30/60/180 min (default **30 min**; **Check now**). KODRA-hosted sites are
  checked by the server even when KODRA is closed; other hosts only while KODRA
  runs (with TLS certificate expiry). **Replay safe flows on the live site**
  runs only flows you mark **Safe to run on the live site**, and only read-only
  flows can be marked. You get an alert banner (and an OS notification on
  desktop) when something that passed starts failing.
- **Reserved paths:** `/__kodra/reporter.js` and `/__kodra/errors` on
  KODRA-hosted sites belong to KODRA; don't put app routes under `/__kodra/`.
