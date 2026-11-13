---
title: แจ้งปัญหาหรือขอฟีเจอร์
---

[← หน้าแรก](index.md)

# แจ้งปัญหาหรือขอฟีเจอร์

ปัญหาและคำขอฟีเจอร์ของ KODRA รับที่ GitHub Issues:
**<https://github.com/ko-system/kodra/issues>** (ต้องมีบัญชี GitHub)

> **issue ทุกอันเป็นข้อมูลสาธารณะ** ใครก็อ่านได้ ห้ามใส่ API key, token (`sk-…`, `sbp_…`,
> `napi_…`, `github_pat_…`), รหัสผ่าน, ไฟล์ `.env`, ข้อมูลลูกค้า หรือข้อมูลส่วนตัว
> ถ้าเผลอโพสต์ไปแล้ว ให้ **ยกเลิก (revoke) key นั้นทันที** แล้วแก้ไข/ลบข้อความ

## วิธีที่แนะนำ: แจ้งจากในแอป

1. เปิด **Help** (ความช่วยเหลือ) ที่แถบด้านข้าง → **Report a Bug** (รายงานบั๊ก)
2. กรอก **What happened?** (อย่างน้อย 10 ตัวอักษร) — เล่าว่าทำอะไร เห็นอะไร และคาดว่าควรเป็นอย่างไร
3. เลือกสิ่งที่จะแนบ:
   - **Basic system information and logs** — เวอร์ชัน KODRA ระบบปฏิบัติการ การตั้งค่าบางส่วน และ log ล่าสุด
     (บอกแค่ว่ามี key ของผู้ให้บริการไหน ไม่ใส่ตัว key)
   - **Chat session** — ข้อความแชตและสำเนาโค้ดของแอป (ต้องเปิดแชตก่อน)
   - **Add a screenshot** — จับภาพหน้าจอ ภาพจะอยู่ใน clipboard ให้วาง (paste) ใน issue เอง
4. กด **Show what will be sent** เพื่อดูข้อมูลทั้งหมดก่อนส่ง
5. กด **Create GitHub issue** — เบราว์เซอร์จะเปิดหน้า issue ใหม่ที่กรอกหัวข้อและรายละเอียดไว้ให้
   แก้หัวข้อ `[bug] <WRITE TITLE HERE>` ให้สั้นและชัด ตรวจอีกครั้งว่าไม่มีข้อมูลลับ แล้วกด **Submit**

### ไฟล์ debug bundle (`kodra-session-*.json`)

ถ้าติ๊ก **Chat session** KODRA จะ**บันทึกเป็นไฟล์ในเครื่อง** ไม่ได้อัปโหลดไปไหน:

- Desktop: หน้าต่าง "Save KODRA debug bundle" (ค่าเริ่มต้นคือโฟลเดอร์ Downloads)
- Web: ดาวน์โหลดผ่านเบราว์เซอร์

ชื่อไฟล์เป็น `kodra-session-<เลขแชต>-<เวลา>.json` และ issue จะระบุชื่อไฟล์ไว้ให้

ไฟล์นี้มีแชตทั้งหมดและสำเนาโค้ดของแอปคุณ จึง**ไม่ควรแนบใน issue สาธารณะ** ให้ส่งแบบส่วนตัว:
กด **Copy message for the admin** แล้วส่งข้อความนั้นพร้อมแนบไฟล์ให้ผู้ดูแล KODRA ของคุณ
(หรือรอผู้ดูแลติดต่อกลับใน issue) แนบใน issue ได้ก็ต่อเมื่อคุณแน่ใจว่าแอปและแชตนั้นไม่มีข้อมูลลับ
และยอมให้เป็นข้อมูลสาธารณะ

ถ้า KODRA ของคุณไม่มีปุ่ม Report a Bug จะมีปุ่ม **Copy diagnostics** แทน — คัดลอกข้อมูลระบบ
การตั้งค่า และ log แล้วส่งให้ผู้ดูแล KODRA ของคุณ

## แจ้งเองบน GitHub

เปิด <https://github.com/ko-system/kodra/issues/new/choose> แล้วเลือก

- **แจ้งปัญหา / Bug report** — กรอกสิ่งที่เกิดขึ้น ขั้นตอน สิ่งที่ควรเกิด เวอร์ชัน KODRA
  (Settings → General → App Version) และใช้ Desktop หรือ Web
- **ขอฟีเจอร์ใหม่ / Feature request**

ก่อนแจ้ง ลองค้นหา issue เดิมก่อน และดู [FAQ](faq.md)

## รายงานที่ดี

- หนึ่ง issue ต่อหนึ่งปัญหา
- ขั้นตอนที่ทำซ้ำได้ (1, 2, 3 …)
- ข้อความ error แบบเต็ม (คัดลอกเป็นข้อความ ไม่ใช่แค่รูป) — ลบ key/token ออกก่อน
- ชื่อโมเดล AI ที่ใช้ ถ้าปัญหาเกี่ยวกับคำตอบของ AI

## ช่องโหว่ด้านความปลอดภัย

อย่าเปิด issue สาธารณะสำหรับช่องโหว่ของ KODRA เอง ให้ใช้
[Report a vulnerability](https://github.com/ko-system/kodra/security/advisories/new)
(GitHub private vulnerability reporting) แทน

---

## English

Report bugs and request features at
**<https://github.com/ko-system/kodra/issues>**. **Issues are public** — never
include API keys or tokens, passwords, `.env` files or personal data; if you
leak a key, revoke it immediately.

**From the app (recommended):** **Help → Report a Bug**, describe what
happened, choose **Basic system information and logs**, **Chat session** and an
optional screenshot (pasted from the clipboard), check **Show what will be
sent**, then **Create GitHub issue**. GitHub opens with the title and body
pre-filled; edit the `[bug] <WRITE TITLE HERE>` title and submit.

**Debug bundle:** with **Chat session** selected, KODRA saves
`kodra-session-<chat>-<time>.json` on your device (save dialog on desktop,
browser download on the web) — nothing is uploaded, and the issue names the
file. It contains your chat and a snapshot of your app's code, so **do not
attach it to the public issue**: use **Copy message for the admin** and send it
privately to your KODRA admin. Builds without an issue tracker show **Copy
diagnostics** instead.

**Directly on GitHub:** <https://github.com/ko-system/kodra/issues/new/choose> →
Bug report (what happened, steps, expected, KODRA version from Settings →
General → App Version, desktop or web) or Feature request. Report security
vulnerabilities privately via
[Report a vulnerability](https://github.com/ko-system/kodra/security/advisories/new).
