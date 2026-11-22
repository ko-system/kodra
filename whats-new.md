---
title: มีอะไรใหม่
---

[← หน้าแรก](index.md)

# มีอะไรใหม่

สรุปฟีเจอร์ที่เพิ่มเข้ามาใน KODRA แต่ละรอบ (ใหม่สุดอยู่บน) แต่ละหัวข้อมีลิงก์ไปคู่มือฉบับเต็ม

## 2026-11-23

### งานตามกำหนดเวลา (Routines)

ให้ KODRA ดูแลแอประหว่างที่คุณไม่อยู่: แท็บ **Configure** (ตั้งค่า) → **งานตามกำหนดเวลา** → **เพิ่มงาน**

- รูปแบบงาน **ตรวจสุขภาพแอป**, **อัปเดตแพ็กเกจ** (minor/patch บนบรานช์แยก เปิด Pull Request ได้
  ไม่ merge อัตโนมัติ) และ **กำหนดเอง** (อ่านอย่างเดียว หรือเอเจนต์บนบรานช์แยก)
- ตั้ง **ทุกวัน** / **ทุกสัปดาห์** พร้อมเขตเวลา รอบที่พลาดจะรันครั้งเดียวเมื่อเปิด KODRA ครั้งถัดไป
- ผลอยู่ในแชตชื่อ "Scheduled: …" พร้อมการแจ้งเตือน และวงเงินสูงสุดต่อรอบ
- เวอร์ชันเว็บ: งานรันแม้คุณออกจากระบบ

→ [งานตามกำหนดเวลา](guides/routines.md)

### ข้อผิดพลาดบนเว็บจริง และสถานะเว็บไซต์จริง

ในแท็บ **เผยแพร่**:

- **รายงานข้อผิดพลาด** (เปิดเอง) — เห็นข้อผิดพลาดที่ผู้เข้าชมจริงเจอ จัดกลุ่มตามสาเหตุ กด **ให้ AI แก้**
  ข้อมูลส่วนตัว (อีเมล เบอร์โทร โทเคน query string คุกกี้ ค่าในฟอร์ม) ถูกลบออกก่อนเก็บ
- **สถานะเว็บไซต์จริง** — ตรวจเว็บทุก 30 นาที (ปรับได้) รันโฟลว์ที่อ่านอย่างเดียวบนเว็บจริงได้
  และแจ้งเตือนเมื่อสิ่งที่เคยใช้ได้เกิดพัง

→ [ข้อผิดพลาดบนเว็บจริง และสถานะเว็บไซต์จริง](guides/production-monitoring.md)

### แอปใหม่ติดตั้งได้ (PWA)

แอปใหม่ติดตั้งลงหน้าจอโฮมได้ทันทีหลังเผยแพร่ มีหน้าออฟไลน์ภาษาไทย/อังกฤษ แจ้งเมื่อมีเวอร์ชันใหม่
สีตาม Brand Studio ไม่แคช `/api` ปิดได้ด้วย `pwa({ enabled: false })`

→ [แอปติดตั้งได้ (PWA)](guides/pwa.md)

### คีย์บริการไทยซิงก์ไป Vercel อัตโนมัติ

ถ้าแอปเชื่อมโปรเจกต์ Vercel ไว้ คีย์ LINE / พร้อมเพย์ / Omise ที่บันทึกจะถูกส่งไปเป็น Environment Variables
ของ Vercel ให้เอง การ์ดแสดง **ซิงก์ไปยัง Vercel แล้ว** หรือปุ่ม **ลองอีกครั้ง**

→ [บริการไทย: ซิงก์ไป Vercel](integrations/thai-services.md#vercel-sync)

## 2026-11-20

### คุมค่าใช้จ่าย AI

- **การใช้งานและค่าใช้จ่าย** (Usage & spending) ใน Settings — ดูยอดที่ API key ของคุณใช้ไป
  และตั้ง **ขีดจำกัดค่าใช้จ่าย** ต่อเทิร์น ต่อวัน ต่อเดือน
- ไอคอนเหรียญ **$X.XX** ที่หัวแชต บอกค่าใช้จ่ายโดยประมาณของแชตนี้
- **Smart routing** ส่งงานเบื้องหลังไปโมเดลที่ถูกกว่าโดยอัตโนมัติ

→ [ค่าใช้จ่าย AI และ Smart routing](guides/spend-and-routing.md)

### บริการไทย: LINE, พร้อมเพย์, Omise

ล็อกอินด้วย LINE, LIFF, บอท LINE OA, QR พร้อมเพย์ และรับชำระผ่าน Omise
ใส่คีย์ที่แท็บ **Configure** ของแอป → **การเชื่อมต่อบริการไทย**

→ [เชื่อมต่อบริการไทย](integrations/thai-services.md)

### ออกแบบ

- แท็บ **แบรนด์** (Brand) — เลือกสี ฟอนต์ไทย 12 คู่ และรูปทรง พร้อม **ตรวจความสม่ำเสมอ**
- ปุ่ม **บล็อก** (Blocks) — ส่วนหน้าเว็บสำเร็จรูป 28 แบบ
- **โหมดอุปกรณ์** (Device Mode) — ดูมือถือ แท็บเล็ต เดสก์ท็อป หรือ **ดูพร้อมกัน**
- **โหมดออกแบบ** (Design Mode) — ย้าย ปรับระยะ ลบ ทำสำเนา และคอมเมนต์ในพรีวิว โดยไม่ใช้เครดิต AI
- **สร้างจากแบบอ้างอิง** (Build from reference) — สร้างหน้าจากรูปภาพหรือเว็บไซต์ตัวอย่าง

→ [แบรนด์และการออกแบบ](guides/brand-and-design.md)

### ตรวจคุณภาพก่อนเผยแพร่

- แท็บ **ฟีเจอร์** (Features) — รายการฟีเจอร์ที่แอปต้องมี พร้อมสถานะว่าใช้ได้จริงไหม
- การ์ดในแท็บ **เทสต์** (Tests): **ตรวจกดทุกปุ่ม**, **ตรวจหน้าตาที่เปลี่ยนไป**,
  **ตรวจระบบเข้าสู่ระบบ**, **API ของแอป**
- การ์ด **ทดสอบแอป** (App Test) ในแชต — AI ลองใช้แอปแบบผู้ใช้จริง พร้อม **ดูรีเพลย์**
- **คะแนนคุณภาพ** (Quality scores) ในแผง Publish
- **พร้อมเผยแพร่หรือยัง** — ตรวจด่วน (ไม่กี่วินาที) หรือตรวจแบบเต็ม (ประมาณ 3–5 นาที)

→ [ตรวจคุณภาพและทดสอบแอป](guides/quality-checks.md)

### เวอร์ชันเว็บ: เชิญผู้ใช้และคอนโซลผู้ดูแล

ผู้ดูแลเชิญผู้ใช้ใหม่ด้วยลิงก์ ตั้งขีดจำกัดรายคน และระงับบัญชีได้จาก **คอนโซลผู้ดูแลระบบ**

→ [เวอร์ชันเว็บ: คำเชิญ และคอนโซลผู้ดูแล](guides/web-admin.md)

---

## English

New on 2026-11-23:

- **Routines:** the app's **Configure** tab → **Routines**. **Health check**,
  **Dependency updates** (minor/patch on a separate branch, optional GitHub PR,
  never merged automatically) and **Custom** (read-only or agent on a branch);
  daily/weekly schedules with a time zone; missed runs run once at the next
  start; results in a "Scheduled: …" chat; per-run spend cap. On the web version
  routines run even when you're signed out → [guide](guides/routines.md).
- **Production errors & Live site health** (Publish tab): opt-in **Error
  reporting** with personal data scrubbed, grouped errors and **Fix with AI**;
  live checks every 30 min by default, safe read-only flow replays and alerts
  when something that passed starts failing →
  [guide](guides/production-monitoring.md).
- **PWA by default:** new apps are installable, with a Thai/English offline
  page and an update toast; turn off with `pwa({ enabled: false })` →
  [guide](guides/pwa.md).
- **Thai integration keys sync to Vercel** when the app is linked to a Vercel
  project (**Synced to Vercel** / **Retry**) →
  [guide](integrations/thai-services.md).

New on 2026-11-20:

- **Spending:** Settings → **Usage & spending** (usage by model/app/activity,
  per-turn/day/month **Spending limits**), a **$X.XX** spend indicator in the chat
  header, and **Smart routing** for background tasks →
  [guide](guides/spend-and-routing.md).
- **Thai integrations:** LINE Login/LIFF, LINE Messaging API, PromptPay QR and
  Omise; keys go in the app's **Configure** tab → **Thai integrations** →
  [guide](integrations/thai-services.md).
- **Design:** **Brand** tab (Brand Studio + consistency check), **Blocks**,
  **Device Mode** (incl. **Side by side**), **Design Mode**, and **Build from
  reference** in the chat **+** menu → [guide](guides/brand-and-design.md).
- **Quality:** **Features** tab, Tests cards (**Click-everything check**,
  **Visual regression**, **Sign-in check**, **API routes**), the **App Test**
  replay card, **Quality scores** in Publish, and the quick/full **Ready to
  publish?** check → [guide](guides/quality-checks.md).
- **Web version:** invite links, admin console, per-user limits and suspension →
  [guide](guides/web-admin.md).
