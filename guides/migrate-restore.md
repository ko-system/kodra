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

- **โค้ดแอป:** ใช้ [GitHub](../integrations/github.md) แล้ว **Import App** ที่เครื่องใหม่
  (เลือก clone จาก GitHub) หรือคัดลอกโฟลเดอร์แอปไปแล้ว Import App จากโฟลเดอร์
  หรืออัปโหลดไฟล์ .zip ด้วย **Upload app (.zip)**
- **API key:** ต้องใส่ใหม่ใน Settings → Model Providers เพราะ key ถูกเข้ารหัสด้วย keychain
  ของเครื่องเดิม ไฟล์การตั้งค่าจากเครื่องอื่นจึงถอดรหัส key ไม่ได้

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
machine, use GitHub or copy the app folder and **Import App**; re-enter API keys,
because they are encrypted with the old machine's keychain.

**Restoring settings from backup:** "KODRA could not read your existing settings
file…" means `user-settings.json` was unreadable and defaults were used. Quit
KODRA, keep a copy of the current `user-settings.json`, then copy
`user-settings.json.bak` (or `backups/v<version>_<time>_upgrade_from_<old>/user-settings.json`,
the newest of the last 3 upgrade backups) over it and restart. The
`user-settings.json.recovery-<time>.bak` file is the unreadable original. Never
attach settings files to a public issue.
