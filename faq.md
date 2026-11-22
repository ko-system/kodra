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

## ทำไมกดเผยแพร่แล้วช้าลง {#publish-slow}

ก่อนเผยแพร่ KODRA ตรวจแอปให้ใน **พร้อมเผยแพร่หรือยัง** ปกติเป็น **ตรวจด่วน** ใช้เวลาไม่กี่วินาที
แต่ถ้ายังไม่เคยตรวจแบบเต็ม หรือการตรวจแบบเต็มครั้งล่าสุดเก่ากว่า 24 ชั่วโมง / โค้ดเปลี่ยนไปเกิน 5 ไฟล์
ระบบจะถาม "ตรวจแบบเต็มก่อนเผยแพร่ไหม?" ซึ่งใช้เวลาประมาณ 3–5 นาที (build จริง ไล่เปิดทุกหน้า
รันเทสต์ของแอป) ถ้ารีบ กด **เผยแพร่ด้วยผลตรวจด่วน** ได้ และถ้าพบปัญหาก็ยังกด **เผยแพร่เลย** ได้
ดู [ตรวจคุณภาพและทดสอบแอป](guides/quality-checks.md)

## เปลี่ยนฟอนต์ / สีของแอปยังไง

เปิดแท็บ **แบรนด์** ในแผง Preview เลือก **คู่ฟอนต์** (รองรับภาษาไทยทั้ง 12 คู่) หรือเลือกฟอนต์ใน
ช่อง **หัวข้อ** / **เนื้อหา** ปรับสีใน **ชุดสี** แล้วกด **ใช้กับแอป** ไม่ใช้เครดิต AI
ดู [แบรนด์และการออกแบบ](guides/brand-and-design.md)

## KODRA ยืนยันการโอนเงินพร้อมเพย์ให้ไหม {#promptpay}

ไม่ได้ QR พร้อมเพย์ยืนยันการชำระเงินเองไม่ได้ เพราะแอปไม่ได้รับแจ้งเมื่อมีเงินเข้า ต้องตรวจยอดในแอปธนาคาร
แล้วยืนยันคำสั่งซื้อเอง หรือใช้ Omise ถ้าต้องการยืนยันอัตโนมัติ ดู [บริการไทย](integrations/thai-services.md)

## ใส่คีย์ LINE / Omise ตรงไหน

แท็บ **Configure** (ตั้งค่า) ในแผง Preview ของแอป → **การเชื่อมต่อบริการไทย** (ไม่ใช่หน้า Settings)
อย่าวางคีย์ลับในแชต

## AI หยุดเองพร้อมข้อความ "หยุดชั่วคราว: ถึงขีดจำกัดค่าใช้จ่าย…"

ถึงขีดจำกัดค่าใช้จ่ายที่ตั้งไว้ กด **ทำต่อไป** หรือ **เพิ่มขีดจำกัด** ถ้าเป็นขีดจำกัดที่ผู้ดูแลระบบกำหนด
(เวอร์ชันเว็บ) ต้องรอเดือนหน้าหรือติดต่อผู้ดูแล ดู [ค่าใช้จ่าย AI](guides/spend-and-routing.md)

## งานตามกำหนดเวลาจะเปลี่ยนแอปที่เผยแพร่อยู่ไหม {#routine-live-app}

ไม่ งานตามกำหนดเวลา (Routines) ไม่แตะบรานช์หลักและไม่เผยแพร่อะไรเอง **ตรวจสุขภาพแอป** และงานแบบ
อ่านอย่างเดียวไม่แก้โค้ดเลย ส่วน **อัปเดตแพ็กเกจ** และ **เอเจนต์บนบรานช์แยก** แก้บนบรานช์
`kodra/routines/…` เท่านั้น และ **ไม่ merge อัตโนมัติ** คุณต้องตรวจแล้วรวมเอง จากนั้นเผยแพร่ตามปกติ
ดู [งานตามกำหนดเวลา](guides/routines.md)

## ทำไมงานตามกำหนดเวลาขึ้นว่า "ข้าม" หรือ "ไม่ได้เริ่ม"

- **แอปกำลังทำงานกับแชตอยู่** — งานรอได้ไม่เกิน 1 ชั่วโมงแล้วข้ามรอบนั้น
- **ใช้ถึงวงเงินรายวัน/รายเดือนแล้ว** — ดู [ค่าใช้จ่าย AI](guides/spend-and-routing.md)
- **แอปมีการเปลี่ยนแปลงที่ยังไม่ได้บันทึก** — งานแบบเอเจนต์บนบรานช์แยกจะไม่เริ่ม บันทึกหรือยกเลิกก่อน

## การรายงานข้อผิดพลาดเก็บข้อมูลอะไรบ้าง {#error-reporting-data}

เก็บชนิดข้อผิดพลาด ข้อความและ stack หน้าที่เกิด (เฉพาะรูปแบบ path) ชื่อเบราว์เซอร์ เวลา จำนวนครั้ง
และเวอร์ชันที่เกิด ส่วนอีเมล เบอร์โทร เลขบัตร โทเคน query string ถูกลบออกตั้งแต่ในเบราว์เซอร์และลบซ้ำ
ที่เซิร์ฟเวอร์ และไม่เก็บคุกกี้ ค่าที่กรอกในฟอร์ม หรือ IP ข้อมูลส่งมาที่ KODRA เท่านั้น
ปิดไว้เป็นค่าเริ่มต้น ดู [ข้อผิดพลาดบนเว็บจริง](guides/production-monitoring.md)

## ทำไมแอปของฉันมีปุ่มติดตั้ง / ไม่อยากให้แอปติดตั้งได้ {#pwa-off}

แอปใหม่เป็น PWA ตั้งแต่แรก ผู้ใช้จึงติดตั้งลงหน้าจอโฮมได้ ถ้าไม่ต้องการ แก้ `vite.config.ts` เป็น
`pwa({ enabled: false })` (หรือบอก AI ว่า *"ปิด PWA"*) แล้วเผยแพร่ใหม่ ดู [แอปติดตั้งได้ (PWA)](guides/pwa.md)

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
- **Publish got slower:** a quick check (seconds) runs first; if there's no
  recent full check, KODRA offers the full check (≈3–5 min). Choose **Publish
  with the quick check** to skip it; failures can still be published anyway
  ([guide](guides/quality-checks.md)).
- **Change fonts/colors:** preview **Brand** tab → **Font pairs** or
  **Headings/Body text**, palette → **Apply to app**
  ([guide](guides/brand-and-design.md)).
- **Does KODRA confirm PromptPay payments?** No. A PromptPay QR can't confirm a
  payment; check your bank app, or use Omise for automatic confirmation
  ([guide](integrations/thai-services.md)). LINE/Omise keys go in the app's
  **Configure** tab → **Thai integrations**.
- **"Paused: … spend limit reached":** **Continue anyway** or **Raise limit**
  ([guide](guides/spend-and-routing.md)).
- **Will a routine change my live app?** No. Routines never touch your main
  branch or publish anything; dependency updates and agent routines work on a
  `kodra/routines/…` branch that is never merged automatically
  ([guide](guides/routines.md)). A routine is skipped if you're chatting for
  over an hour, or not started when a spend limit is reached or (agent on a
  branch) the app has uncommitted changes.
- **What does error reporting collect?** Error kind, message and stack, page
  route shape, browser family, time, count and release. Emails, phone numbers,
  tokens and query strings are scrubbed; cookies, form values and IPs are never
  stored. Off by default ([guide](guides/production-monitoring.md)).
- **How do I stop my app from being installable?** Set `pwa({ enabled: false })`
  in `vite.config.ts` and publish again ([guide](guides/pwa.md)).
- **Still stuck:** [report a problem](report-a-problem.md).
