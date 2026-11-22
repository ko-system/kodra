---
title: มีอะไรใหม่ (2026-11-20)
---

[← หน้าแรก](index.md)

# มีอะไรใหม่ (2026-11-20)

สรุปฟีเจอร์ที่เพิ่มเข้ามาใน KODRA รอบนี้ แต่ละหัวข้อมีลิงก์ไปคู่มือฉบับเต็ม

## คุมค่าใช้จ่าย AI

- **การใช้งานและค่าใช้จ่าย** (Usage & spending) ใน Settings — ดูยอดที่ API key ของคุณใช้ไป
  และตั้ง **ขีดจำกัดค่าใช้จ่าย** ต่อเทิร์น ต่อวัน ต่อเดือน
- ไอคอนเหรียญ **$X.XX** ที่หัวแชต บอกค่าใช้จ่ายโดยประมาณของแชตนี้
- **Smart routing** ส่งงานเบื้องหลังไปโมเดลที่ถูกกว่าโดยอัตโนมัติ

→ [ค่าใช้จ่าย AI และ Smart routing](guides/spend-and-routing.md)

## บริการไทย: LINE, พร้อมเพย์, Omise

ล็อกอินด้วย LINE, LIFF, บอท LINE OA, QR พร้อมเพย์ และรับชำระผ่าน Omise
ใส่คีย์ที่แท็บ **Configure** ของแอป → **การเชื่อมต่อบริการไทย**

→ [เชื่อมต่อบริการไทย](integrations/thai-services.md)

## ออกแบบ

- แท็บ **แบรนด์** (Brand) — เลือกสี ฟอนต์ไทย 12 คู่ และรูปทรง พร้อม **ตรวจความสม่ำเสมอ**
- ปุ่ม **บล็อก** (Blocks) — ส่วนหน้าเว็บสำเร็จรูป 28 แบบ
- **โหมดอุปกรณ์** (Device Mode) — ดูมือถือ แท็บเล็ต เดสก์ท็อป หรือ **ดูพร้อมกัน**
- **โหมดออกแบบ** (Design Mode) — ย้าย ปรับระยะ ลบ ทำสำเนา และคอมเมนต์ในพรีวิว โดยไม่ใช้เครดิต AI
- **สร้างจากแบบอ้างอิง** (Build from reference) — สร้างหน้าจากรูปภาพหรือเว็บไซต์ตัวอย่าง

→ [แบรนด์และการออกแบบ](guides/brand-and-design.md)

## ตรวจคุณภาพก่อนเผยแพร่

- แท็บ **ฟีเจอร์** (Features) — รายการฟีเจอร์ที่แอปต้องมี พร้อมสถานะว่าใช้ได้จริงไหม
- การ์ดในแท็บ **เทสต์** (Tests): **ตรวจกดทุกปุ่ม**, **ตรวจหน้าตาที่เปลี่ยนไป**,
  **ตรวจระบบเข้าสู่ระบบ**, **API ของแอป**
- การ์ด **ทดสอบแอป** (App Test) ในแชต — AI ลองใช้แอปแบบผู้ใช้จริง พร้อม **ดูรีเพลย์**
- **คะแนนคุณภาพ** (Quality scores) ในแผง Publish
- **พร้อมเผยแพร่หรือยัง** — ตรวจด่วน (ไม่กี่วินาที) หรือตรวจแบบเต็ม (ประมาณ 3–5 นาที)

→ [ตรวจคุณภาพและทดสอบแอป](guides/quality-checks.md)

## เวอร์ชันเว็บ: เชิญผู้ใช้และคอนโซลผู้ดูแล

ผู้ดูแลเชิญผู้ใช้ใหม่ด้วยลิงก์ ตั้งขีดจำกัดรายคน และระงับบัญชีได้จาก **คอนโซลผู้ดูแลระบบ**

→ [เวอร์ชันเว็บ: คำเชิญ และคอนโซลผู้ดูแล](guides/web-admin.md)

---

## English

New in this release (2026-11-20):

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
