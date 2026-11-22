---
title: ค่าใช้จ่าย AI และ Smart routing
---

[← หน้าแรก](../index.md)

# ค่าใช้จ่าย AI และ Smart routing

KODRA ประมาณค่าใช้จ่ายของ key ผู้ให้บริการ AI ที่คุณใส่เอง (BYOK) ให้ดูได้ตลอด
ตั้งขีดจำกัดเพื่อให้เอเจนต์หยุดก่อนใช้เงินเกินได้ และประหยัดค่า AI ด้วย Smart routing

## ดูว่าใช้ไปเท่าไร

- **ในแชต:** ไอคอนเหรียญและยอด **$X.XX** ที่หัวแชต (ขึ้นหลังจาก AI ตอบครั้งแรก) กดเพื่อดู
  **ค่าใช้จ่ายโดยประมาณ (ราคาประกาศ, USD)** แยกเป็น แชทนี้ / แอปนี้ / วันนี้ / เดือนนี้
- **ภาพรวม:** **Settings → การใช้งานและค่าใช้จ่าย** (Usage & spending) ส่วน **การใช้งาน** (Usage)
  แสดงยอด วันนี้, 7 วันที่ผ่านมา, 30 วันที่ผ่านมา, เดือนนี้ และตาราง ตามโมเดล / ตามแอป /
  ตามกิจกรรม (เอเจนต์, เอเจนต์ย่อย, ทีม AI, การย่อบทสนทนา, บอทช่วยเหลือ ฯลฯ)

ยอดเป็นการประมาณเป็น USD จากจำนวนโทเค็นตามราคาประกาศ **ใบแจ้งหนี้ของผู้ให้บริการคือยอดจริง**
ไม่รวมโมเดลแบบสมัครสมาชิก (ChatGPT, Claude Code) โมเดลในเครื่อง (Ollama, LM Studio) และโมเดลฟรี
ของ OpenRouter นับเป็น $0 ส่วนโมเดลที่ไม่ทราบราคาจะแสดง "ไม่ทราบราคา" และไม่ถูกนับรวม

## ตั้งขีดจำกัดค่าใช้จ่าย

1. ไปที่ **Settings → การใช้งานและค่าใช้จ่าย → ขีดจำกัดค่าใช้จ่าย** (Spending limits)
2. กรอกจำนวนเงิน (USD) ในช่องที่ต้องการ: **ต่อเทิร์น**, **ต่อวัน**, **ต่อเดือน**
   เว้นว่าง = ไม่จำกัด (ค่าเริ่มต้นคือปิดทั้งหมด)
3. ถ้าต้องการ ตั้ง **ระดับความพยายามสูงสุด** (Max effort level) เพื่อจำกัดระดับ reasoning
   ของทุกโมเดลและเอเจนต์ย่อย

เมื่อใช้ถึง 80% จะมีข้อความเตือน เมื่อถึง 100% เอเจนต์จะ **หยุดก่อนขั้นตอนถัดไป** และแสดงการ์ดในแชต
เช่น "หยุดชั่วคราว: ถึงขีดจำกัดค่าใช้จ่ายรายวัน" พร้อมปุ่ม

- **ทำต่อไป** (Continue anyway) — ทำงานต่อ (ขีดจำกัดรายวัน/รายเดือนจะไม่หยุดอีกจนสิ้นวัน/สิ้นเดือน)
- **เพิ่มขีดจำกัด** (Raise limit) — เปิดหน้าตั้งค่าเพื่อปรับยอด

เอเจนต์ย่อยและทีม AI นับรวมในเทิร์นเดียวกัน วันและเดือนนับตามเวลาของเครื่องคุณ

> เวอร์ชันเว็บ: ผู้ดูแลอาจตั้ง **ขีดจำกัดที่ผู้ดูแลระบบกำหนด** ไว้ด้วย คุณเพิ่มหรือปิดเองไม่ได้
> ดู [เวอร์ชันเว็บ: คำเชิญ และคอนโซลผู้ดูแล](web-admin.md)

## Smart routing (ประหยัดค่า AI)

Smart routing ส่งงานเบื้องหลัง — เอเจนต์ย่อย (sub-agent), การย่อบทสนทนา และการตรวจดีไซน์ —
ไปให้โมเดลที่ถูกกว่าจาก **ผู้ให้บริการและ key เดียวกัน** (เช่น Claude Opus → Claude Haiku)
งานหลักและการเขียนโค้ดยังใช้โมเดลที่คุณเลือกเสมอ

- ตั้งค่าที่ **Settings → AI → Smart routing** เลือก **สมดุล (แนะนำ)** (ค่าเริ่มต้น) หรือ **ปิด**
- ดูยอดที่ประหยัดได้ในหน้า การใช้งานและค่าใช้จ่าย และในกล่องค่าใช้จ่ายของแชต
- ถ้า key ของคุณใช้โมเดลที่ถูกกว่าไม่ได้ KODRA จะใช้โมเดลที่คุณเลือกแทนโดยอัตโนมัติ
  (ไม่มี error แต่งานนั้นจะไม่ได้ประหยัด)
- ไม่มีผลกับโมเดลแบบสมัครสมาชิก โมเดลในเครื่อง โมเดลฟรี หรือโมเดลที่เพิ่มเอง

---

## English

- **See spend:** the coin **$X.XX** in the chat header opens **Estimated spend
  (list prices, USD)** for this chat / app / today / month. **Settings → Usage &
  spending** shows usage tiles and tables by model, app and activity. Figures
  are estimates at list prices; your provider's bill is authoritative.
  Subscription models are excluded; unknown-price models are not counted.
- **Spending limits:** Settings → Usage & spending → **Spending limits**: **Per
  turn / Per day / Per month (USD)**, empty = no limit. KODRA warns at 80% and
  pauses the agent before its next step at 100%, with **Continue anyway** and
  **Raise limit**. **Max effort level** caps reasoning effort.
- **Smart routing:** Settings → AI → **Smart routing**, **Balanced
  (recommended)** (default) or **Off**. Sub-agents, compaction and the design
  check go to a cheaper model from the same provider and key; the main agent
  always uses your chosen model. If your key can't use the cheaper model, KODRA
  uses your chosen model instead.
