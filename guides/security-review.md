---
title: ตรวจความปลอดภัย (Security Review)
---

[← หน้าแรก](../index.md)

# ตรวจความปลอดภัย (Security Review)

Security Review ให้ AI อ่านโค้ดแอปของคุณเพื่อหาช่องโหว่ แล้วสรุปเป็นรายการพร้อมระดับความรุนแรง
และวิธีแก้ ควรรันก่อนเผยแพร่แอปที่มีการล็อกอินหรือเก็บข้อมูลผู้ใช้

## วิธีใช้

1. เปิดแท็บ **Security** ในแผง Preview
2. กด **Run review** (หรือ **Run Security Review** ถ้ายังไม่เคยรัน)
   KODRA จะเปิดแชตใหม่และให้ AI ตรวจโค้ด
3. เมื่อเสร็จ แท็บ Security จะแสดงรายการที่พบ แต่ละรายการบอก **What** (ปัญหาคืออะไร),
   **Risk** (ความเสี่ยง), **Potential Solutions** และ **Relevant Files**

## สิ่งที่ตรวจ

- การยืนยันตัวตนและสิทธิ์การเข้าถึง (authentication / authorization)
- injection: SQL, XSS, command injection
- API ที่ไม่ต้องล็อกอินก็เรียกได้ หรือเข้าถึงข้อมูลของคนอื่นได้ (IDOR)
- secret หรือ private key ที่หลุดไปฝั่งเบราว์เซอร์ (key แบบ public เช่น Supabase anon key ไม่นับเป็นปัญหา)

## ระดับความรุนแรง

| ระดับ | ความหมาย |
|---|---|
| **critical** | โจมตีได้ง่ายมาก ระบบถูกยึดได้ทั้งหมด |
| **high** | โจมตีได้ในบางเงื่อนไข |
| **medium** | ต้องใช้หลายขั้นตอนจึงโจมตีได้ |
| **low** | ไม่ตรงแนวปฏิบัติที่ดี |

## แก้ไข

- กด **Fix Issue** ที่รายการที่ต้องการ หรือเลือกหลายรายการแล้วกด **Fix … issues** / **Fix all issues**
- KODRA จะเปิดแชตสำหรับแก้ไข ดูผลได้ที่ **Show fix for …** และสั่งแก้ใหม่ด้วย **Re-run fix**
- แก้แล้วให้กด **Run review** อีกครั้งเพื่อตรวจซ้ำ

## ปรับกฎการตรวจ

กด **Edit rules** เพื่อเขียนบริบทให้ AI ใช้ทุกครั้งที่ตรวจ ระบบจะบันทึกเป็นไฟล์
`SECURITY_RULES.md` ในแอป เช่น:

- ความเสี่ยงที่ยอมรับแล้ว และสิ่งที่ไม่ต้องรายงาน
- สภาพแวดล้อมที่ใช้งาน (เช่น ใช้ภายในองค์กรเท่านั้น)
- ข้อกำหนดเฉพาะของแอป

> Security Review ช่วยลดความเสี่ยงได้ แต่ไม่ใช่การรับรองความปลอดภัย แอปที่เก็บข้อมูลสำคัญ
> ควรให้ผู้เชี่ยวชาญตรวจเพิ่ม

---

## English

The **Security** tab in the preview panel runs an AI review of your app's code.
Click **Run review**; KODRA opens a new chat that inspects the code and lists
findings with **What / Risk / Potential Solutions / Relevant Files** and a
severity (**critical**, **high**, **medium**, **low**). It checks auth and
authorization, injection (SQL, XSS, command), unauthenticated or IDOR-prone APIs,
and secrets exposed to the browser (public keys such as the Supabase anon key are
fine). Use **Fix Issue** / **Fix all issues** to open a fix chat, then re-run the
review. **Edit rules** saves extra context (accepted risks, non-issues,
environment) to `SECURITY_RULES.md`. It is not a substitute for a professional
audit.
