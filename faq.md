---
title: คำถามที่พบบ่อย (FAQ)
---

[← หน้าแรก](index.md)

# คำถามที่พบบ่อย (FAQ)

## AI ตอบกลับเป็นกล่องสีแดง "Sorry, there was an error from the AI" {#ai-error}

ข้อความต่อจากนั้นมาจากผู้ให้บริการ AI โดยตรง สาเหตุที่พบบ่อย:

- **API key ผิดหรือหมดอายุ** — ไปที่ Settings → Model Providers แล้วกด **Test Key**
  ถ้าไม่ผ่านให้สร้าง key ใหม่แล้ว **Save Key**
- **เครดิตหมด / ยังไม่ผูกบัตร** — ตรวจหน้า billing ของผู้ให้บริการ
- **เกินโควตา (429 / rate limit / "Resource has been exhausted")** — ดู
  [AI ตอบว่าเกินโควตา](help/ai-rate-limit.md)
- **"This model doesn't have a free quota tier"** — โมเดลนี้ไม่มีโควตาฟรี ให้เลือกโมเดลอื่น
  หรือเปิด billing กับผู้ให้บริการ
- **ข้อความยาวเกิน context ของโมเดล** — เริ่มแชตใหม่ หรือเลือกโมเดลที่รองรับ context ยาวกว่า

## ใช้โควตา Basic Agent ฟรีของวันนี้หมดแล้ว

ข้อความ "You have used all … free Basic Agent messages for today" หมายถึงใช้ครบโควตารายวัน
ข้อความนั้นยังไม่ได้ส่ง กด **Switch to Build** เพื่อส่งในโหมด Build แทน หรือรอโควตารีเซ็ตตามเวลาที่แสดง
หรือเพิ่ม API key ของคุณเองใน Model Providers

## Preview ไม่ขึ้น / ขึ้นหน้าขาว

1. ดูแท็บ **Problems** ว่ามี error จาก TypeScript หรือ build หรือไม่ แล้วบอก AI ให้แก้
2. เมนู **More** ในแผง Preview → **Rebuild** (ติดตั้ง `node_modules` ใหม่)
3. ยังไม่หาย ลอง **Clear Cache** แล้ว **Recreate Sandbox**
4. ถ้ามีแถบเตือนเรื่อง pnpm ดู [ย้ายไป pnpm 11](upgrades/pnpm-migration.md)

## AI แก้แล้วแอปพัง อยากย้อนกลับ

กด **Undo** ใต้ข้อความล่าสุดของ AI หรือเปิด **Version History** (กด "Version N" ที่หัวแชต)
แล้ว **Restore to this version**

## แอปของฉันเก็บไว้ที่ไหน

- Desktop: `~/kodra-apps/<ชื่อแอป>` (ถ้าย้ายมาจาก Dyad จะใช้โฟลเดอร์เดิม `~/dyad-apps` ต่อ)
- Web: บนเซิร์ฟเวอร์ของ KODRA เชื่อม [GitHub](integrations/github.md) เพื่อเก็บสำเนาโค้ดใน repo ของคุณ

## ดูเวอร์ชัน KODRA ได้ที่ไหน

**Settings → General → App Version**

## ใช้ Supabase และ Neon ในแอปเดียวกันได้ไหม

ไม่ได้ เปิดได้ครั้งละหนึ่งฐานข้อมูลต่อแอป ("Only one database integration can be active at a time.")

## AI ค้นเว็บไม่ได้ / สร้างรูปไม่ได้

ต้องใส่ key ของคุณเอง ดู [ค้นหาเว็บและสร้างรูปภาพ](guides/byok-tools.md)

## ยังไม่หาย

[แจ้งปัญหา](report-a-problem.md) — ใช้ **Help → Report a Bug** ในแอป

---

## English

- **Red "Sorry, there was an error from the AI" box:** the rest of the message
  comes from your AI provider. Check the key (Settings → Model Providers → **Test
  Key**), billing/credits, rate limits ([guide](help/ai-rate-limit.md)), or pick
  another model if it "doesn't have a free quota tier". Start a new chat if the
  conversation is too long for the model.
- **Basic Agent daily quota used up:** the message was not sent; **Switch to
  Build**, wait for the reset time, or add your own key.
- **Preview blank:** check the **Problems** tab, then Preview → **More** →
  **Rebuild**, **Clear Cache**, **Recreate Sandbox**.
- **Go back:** **Undo**, or **Version History → Restore to this version**.
- **Where apps live:** desktop `~/kodra-apps` (installs migrated from Dyad keep `~/dyad-apps`);
  web: on the KODRA server.
- **Version:** Settings → General → App Version.
- **Supabase + Neon together:** not supported; one database integration per app.
- **Still stuck:** [report a problem](report-a-problem.md).
