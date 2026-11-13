---
title: เชื่อมต่อ Supabase
---

[← หน้าแรก](../index.md)

# เชื่อมต่อ Supabase

[Supabase](https://supabase.com) ให้ฐานข้อมูล Postgres, ระบบล็อกอิน, storage และ edge functions
กับแอปของคุณ KODRA เชื่อมด้วย **personal access token** ของบัญชี Supabase

## ขั้นตอน

1. ในแอปที่ต้องการ กดเชื่อมต่อ Supabase จะเปิดหน้าต่าง **Connect Supabase**
2. กด **Open Supabase tokens** (ไปที่ <https://supabase.com/dashboard/account/tokens>)
3. กด **Generate new token** ตั้งชื่อ เช่น `KODRA`
4. คัดลอก token (ขึ้นต้นด้วย `sbp_`) มาวางในช่อง **Personal access token** แล้วกด **Connect**
   KODRA จะตรวจ token กับ Supabase ก่อนบันทึก และเก็บแบบเข้ารหัส
5. เลือกโปรเจกต์ใน **Supabase Projects** หรือกด **Create new project**
   (KODRA สร้างรหัสผ่านฐานข้อมูลให้)

### token นี้ทำอะไรได้

personal access token มีสิทธิ์เท่ากับบัญชีของคุณใน**ทุก organization** ที่คุณเป็นสมาชิก
KODRA ใช้เพื่อดูรายการ organization/โปรเจกต์, สร้างโปรเจกต์, รัน SQL และ deploy edge functions
ยกเลิก token ได้ทุกเมื่อที่หน้าเดียวกัน (ถ้ายกเลิก ต้องเชื่อมใหม่ใน KODRA)

> ห้ามวาง token ในแชตกับ AI หรือใน GitHub issue

### หลังเชื่อมต่อ

- **Add Organization** — เพิ่ม organization อื่น
- **Database Branch** — เลือก branch ของฐานข้อมูล
- **Update app's API key** — อัปเดต key ของโปรเจกต์ในแอป
- **Redeploy edge functions** — deploy edge functions ใหม่
- **Write SQL migration files** — ให้ AI บันทึกการเปลี่ยนแปลงฐานข้อมูลเป็นไฟล์ migration ในแอปด้วย

แอปหนึ่งใช้ Supabase หรือ [Neon](neon.md) ได้อย่างใดอย่างหนึ่งเท่านั้น

### เคยเชื่อมด้วย "browser sign-in"

ถ้าเห็น "Connected with browser sign-in. That sign-in can't be renewed in this version of KODRA…"
ให้กด **Reconnect with access token** แล้วทำตามขั้นตอนข้างบน

## ไม่พบ publishable key {#no-publishable-keys}

ข้อความ: **"KODRA couldn't find a publishable key for this Supabase project. It may be paused or
connected through the wrong Supabase account."**

KODRA ดึง API key ของโปรเจกต์ได้ แต่ไม่มี publishable key ที่ใช้งานได้ สาเหตุที่พบบ่อย:

1. **โปรเจกต์ถูก pause** (โปรเจกต์ฟรีที่ไม่ได้ใช้งานนานจะถูกพักอัตโนมัติ) — เปิด
   <https://supabase.com/dashboard> เลือกโปรเจกต์ แล้วกด **Restore / Resume project**
   รอให้พร้อมใช้งาน แล้วลองใหม่ใน KODRA
2. **เชื่อมด้วยบัญชี Supabase ผิด** — token เป็นของบัญชีที่ไม่ได้เป็นเจ้าของโปรเจกต์
   ให้สร้าง token จากบัญชีที่เป็นเจ้าของ แล้วเชื่อมใหม่ หรือเลือกโปรเจกต์ที่ถูกต้อง
3. **ยังไม่มี publishable key** — ในหน้า Project Settings → API Keys ของ Supabase
   ตรวจว่ามี publishable key แล้ว (ถ้าไม่มีให้สร้าง) จากนั้นกด **Update app's API key** ใน KODRA

---

## English

KODRA connects to Supabase with a **personal access token**: click **Open
Supabase tokens** (<https://supabase.com/dashboard/account/tokens>) → **Generate
new token** (name it "KODRA") → paste the `sbp_…` token into **Personal access
token** → **Connect**. KODRA validates and stores it encrypted, then you pick a
project or **Create new project**. The token acts as your account in every
organization you belong to; KODRA uses it to list orgs/projects, create
projects, run SQL and deploy edge functions. Revoke it on the same page any time.
Never paste it into a chat or issue. An app can use Supabase or Neon, not both.
Old browser sign-ins must use **Reconnect with access token**.

**No publishable key** ("KODRA couldn't find a publishable key for this
Supabase project…"): resume the project if it is paused (Supabase dashboard →
project → Restore), reconnect with the Supabase account that owns the project,
or create a publishable key under Project Settings → API Keys and click
**Update app's API key**.
