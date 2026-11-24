---
title: ย้ายข้อมูลและกู้คืนการตั้งค่า
---

[← หน้าแรก](../index.md)

# ย้ายข้อมูลและกู้คืนการตั้งค่า

หน้านี้ใช้กับ **KODRA Desktop** (เวอร์ชัน Web เก็บการตั้งค่าบนเซิร์ฟเวอร์ ถ้ามีปัญหาให้ติดต่อผู้ดูแล)

## โฟลเดอร์ข้อมูลของ KODRA

| ระบบ | โฟลเดอร์ข้อมูล (userData) |
|---|---|
| macOS | `~/Library/Application Support/KODRA` |
| Windows | `%APPDATA%\KODRA` |
| Linux | `~/.config/KODRA` |

ในโฟลเดอร์นี้มี `user-settings.json` (การตั้งค่า), `sqlite.db` (รายการแอปและแชต) และโฟลเดอร์
`backups/` ส่วนโค้ดของแอปอยู่ที่ `~/kodra-apps` (ค่าเริ่มต้น)

## ย้ายมาจาก Dyad

ครั้งแรกที่เปิด KODRA ระบบจะคัดลอกข้อมูลจากโฟลเดอร์ `dyad` เดิม (เช่น
`~/Library/Application Support/dyad`) มาไว้ในโฟลเดอร์ `KODRA` ให้อัตโนมัติหนึ่งครั้ง
โฟลเดอร์เดิมจะไม่ถูกแก้ไข และ KODRA จะใช้โฟลเดอร์แอปเดิม `~/dyad-apps` ต่อไป (ทั้งแอปเก่าและแอปใหม่)

## ย้ายไปเครื่องใหม่

### ย้ายทุกอย่างในครั้งเดียว (แนะนำ)

1. เครื่องเดิม: **Settings → สำรองและย้ายเครื่อง → ส่งออกทั้งหมด** แล้วกด **ส่งออก…**
   เลือกที่บันทึกไฟล์ `.kodrabackup`
   - ถ้าไม่อยากกรอก API key ใหม่ ให้ติ๊ก **รวม API key และการเชื่อมต่อบัญชี โดยล็อกด้วยรหัสผ่าน**
     แล้วตั้งรหัสผ่าน (KODRA กู้รหัสผ่านนี้คืนให้ไม่ได้ ถ้าลืมต้องกรอก key ใหม่เองทั้งหมด)
   - ติ๊ก/ไม่ติ๊ก **รวมประวัติแชต** ได้ตามต้องการ
2. คัดลอกไฟล์ไปเครื่องใหม่ ไฟล์นี้มีโค้ดและไฟล์ `.env` ของแอป ให้เก็บอย่างปลอดภัย
3. เครื่องใหม่: **Settings → สำรองและย้ายเครื่อง → นำเข้าจากไฟล์สำรอง** กด **เลือกไฟล์สำรอง…**
   ระบบจะตรวจว่าไฟล์ครบถ้วนก่อน แล้วเลือกวิธีนำเข้า:
   - **เพิ่มเข้าไปในของที่มีอยู่** — เก็บแอปและแชตเดิมไว้ แอปชื่อซ้ำจะมีตัวเลขต่อท้าย เช่น “Todo 2”
   - **แทนที่ของที่มีอยู่** — ข้อมูลปัจจุบันถูกย้ายไปเก็บในโฟลเดอร์ `before-import-<เวลา>`
     ในโฟลเดอร์ข้อมูลของ KODRA (ไม่ลบทิ้ง) แล้ว KODRA จะเริ่มใหม่
4. กด **นำเข้า** แล้วกรอก key ที่ระบบแจ้งไว้ในหน้าสรุป (ถ้าไม่ได้ล็อกรวมไว้ในไฟล์)

ไม่รวมในไฟล์: `node_modules` และไฟล์ build (สร้างใหม่เองตอนรันแอป), ฐานข้อมูลในตัว
(Local Postgres), การเข้าสู่ระบบ ChatGPT

### ส่งออกแอปเดียว

หน้ารายละเอียดแอป → ⋮ → **ส่งออกเป็น .zip** (ไม่รวม `node_modules` และไฟล์ `.env`) แล้วใช้
**Upload app (.zip)** ที่เครื่องปลายทาง

### วิธีอื่น

- **โค้ดแอป:** ใช้ [GitHub](../integrations/github.md) แล้ว **Import App** ที่เครื่องใหม่
  (เลือก clone จาก GitHub) หรือคัดลอกโฟลเดอร์แอปไปแล้ว Import App จากโฟลเดอร์
- **API key:** ถ้าไม่ได้ใช้ไฟล์สำรองแบบล็อกรหัสผ่าน ต้องใส่ใหม่ใน Settings → Model Providers
  เพราะ key ถูกเข้ารหัสด้วย keychain ของเครื่องเดิม

## กู้คืนการตั้งค่าจาก backup {#restoring-settings-from-backup}

ถ้าเห็นข้อความ **"KODRA could not read your existing settings file, so it fell back to default
settings."** แปลว่าไฟล์ `user-settings.json` อ่านไม่ได้ (เช่น เสียหาย) KODRA จึงใช้ค่าเริ่มต้นแทน
แต่ได้เก็บไฟล์เดิมไว้ให้แล้ว

ไฟล์ backup ในโฟลเดอร์ข้อมูล:

| ไฟล์ | คืออะไร |
|---|---|
| `user-settings.json.recovery-<เวลา>.bak` | ไฟล์ที่อ่านไม่ได้ ถูกเก็บไว้ก่อนเขียนทับ |
| `user-settings.json.bak` | สำเนาการตั้งค่าก่อนการบันทึกครั้งล่าสุด |
| `backups/v<เวอร์ชัน>_<เวลา>_upgrade_from_<เวอร์ชันเดิม>/user-settings.json` | backup อัตโนมัติทุกครั้งที่อัปเดตเวอร์ชัน (เก็บ 3 ชุดล่าสุด พร้อม `sqlite.db`) |

ขั้นตอนกู้คืน:

1. **ปิด KODRA ให้สนิท**
2. เปิดโฟลเดอร์ข้อมูลตามตารางด้านบน
3. สำรองไฟล์ `user-settings.json` ปัจจุบันไว้ก่อน (เช่น เปลี่ยนชื่อเป็น `user-settings.json.current`)
4. คัดลอกไฟล์ backup ที่ต้องการ (เริ่มจาก `user-settings.json.bak` หรือไฟล์ใน `backups/` ที่ใหม่ที่สุด)
   มาวางและเปลี่ยนชื่อเป็น `user-settings.json`
5. เปิด KODRA ใหม่ แล้วตรวจการตั้งค่าและ API key ใน Settings → Model Providers

ไฟล์ `.recovery-…bak` คือไฟล์ที่เสีย อาจกู้ไม่ได้ ใช้เป็นทางเลือกสุดท้าย
ถ้ากู้ไม่ได้ ให้ตั้งค่าใหม่และใส่ API key ใหม่ แล้ว [แจ้งปัญหา](../report-a-problem.md)
(อย่าแนบไฟล์การตั้งค่าใน issue เพราะอาจมีข้อมูลลับ)

---

## English

Desktop only. KODRA's data folder is `~/Library/Application Support/KODRA`
(macOS), `%APPDATA%\KODRA` (Windows) or `~/.config/KODRA` (Linux); app code
lives in `~/kodra-apps`. On first launch KODRA copies the old `dyad` data folder
once and never changes it, and keeps using the old `~/dyad-apps` apps folder. To move to a new
machine, use **Settings → Backup & move → Export everything** (one `.kodrabackup` file with all apps, chats and settings) and **Import from export** on the new machine. API keys are left out unless you protect them with a password. With existing data choose **Add to what's here** (duplicate names get a number) or **Replace what's here** (old data is kept in `before-import-<time>` and KODRA restarts). Dependencies, build output, built-in databases and ChatGPT sign-in are not included. A single app can be exported from its details page (⋮ → **Export as .zip**).

**Restoring settings from backup:** "KODRA could not read your existing settings
file…" means `user-settings.json` was unreadable and defaults were used. Quit
KODRA, keep a copy of the current `user-settings.json`, then copy
`user-settings.json.bak` (or `backups/v<version>_<time>_upgrade_from_<old>/user-settings.json`,
the newest of the last 3 upgrade backups) over it and restart. The
`user-settings.json.recovery-<time>.bak` file is the unreadable original. Never
attach settings files to a public issue.
