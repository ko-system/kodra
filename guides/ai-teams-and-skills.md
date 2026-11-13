---
title: ทีม AI และสกิล
---

[← หน้าแรก](../index.md)

# ทีม AI และสกิล

## ทีม AI

เมื่อคุณสั่งงานใหญ่ในโหมด **Agent** (เช่น "ทำระบบร้านค้าออนไลน์ มีตะกร้า ชำระเงิน และหน้าแอดมิน")
KODRA จะวางแผนแบ่งงานเป็นงานย่อย แล้วให้ AI หลายตัวทำพร้อมกัน แต่ละตัวมีบทบาท เช่น
**Read-only** (อ่าน/สำรวจโค้ด), **Writer** (เขียนโค้ด) และ **Reviewer** (ตรวจงาน)

### เริ่มใช้งาน

- ไม่ต้องตั้งค่าอะไร KODRA จะตั้งทีมเองเมื่องานใหญ่พอ
- หรือเปิดแท็บ **AI Team** (ทีม AI) ในแผง Preview แล้วกด **Plan this with a team**
  ระบบจะเติม "Plan this with an AI team: " ในช่องพิมพ์ให้ พิมพ์งานต่อแล้วส่ง

### ติดตามงาน

- แท็บ **AI Team** แสดงสมาชิกและงานแยกตามสถานะ: In progress, Up next,
  Waiting on other tasks, Done, Failed or cancelled พร้อมจำนวนงานที่เสร็จแล้ว
- เหนือช่องพิมพ์จะมีแถบ **AI Team · N working** และในแชตจะมีการ์ด **AI team plan**
- กด **Stop** เพื่อหยุดสมาชิกคนเดียว หรือ **Stop team** เพื่อหยุดทั้งทีม
- ถ้าทีมหยุดกลางทาง ("Paused — N tasks left") ส่งข้อความใหม่เพื่อทำต่อ

### ตั้งค่า (Settings → Experiments → AI team)

| ตัวเลือก | ค่าเริ่มต้น | ความหมาย |
|---|---|---|
| **Use AI teams for bigger requests** | เปิด | ให้ตั้งทีมสำหรับงานใหญ่ (ใช้เครดิต API มากขึ้น) |
| **Agents working at once** | 3 | จำนวน AI ที่ทำงานพร้อมกัน ลดลงถ้าเจอ [rate limit](../help/ai-rate-limit.md) |
| **Install skills automatically** | เปิด | ให้ติดตั้งสกิลจากคลังสกิลของ KODRA เมื่องานต้องใช้ |

ข้อจำกัด:
- ถ้าปิดฟีเจอร์ไว้ จะเห็น "AI teams are turned off" → กด **Turn on in Settings**
- ทีมต้องใช้โมเดลที่ KODRA เรียกได้โดยตรง (ใช้กับแชต Claude Code ไม่ได้) จะเห็นปุ่ม **Change model**
- ทีม AI เรียกโมเดลหลายครั้งพร้อมกัน ค่าใช้จ่ายจึงสูงกว่าการทำงานคนเดียว

## สกิล (Skills)

สกิลคือคู่มือเฉพาะเรื่องที่ AI โหลดมาใช้ระหว่างทำงาน เช่น การทำระบบล็อกอิน หรือการทำหน้าเว็บให้รองรับมือถือ

- **สกิลในตัว:** add-authentication, add-email-verification, add-password-reset,
  design-system, design-patterns, local-postgres, publish-site
- **คลังสกิล (Catalog):** มาจาก [ko-system/kodra-skills](https://github.com/ko-system/kodra-skills)
  เช่น landing-page, responsive-layout, accessibility-audit, seo-metadata,
  forms-validation, crud-dashboard, ecommerce-checkout, thai-localization,
  performance-web-vitals, qa-smoke-tests

### จัดการสกิล

เปิดเมนู **Skills** (สกิล) ที่แถบด้านข้าง

- แท็บ **Installed** — สกิลที่ติดตั้งแล้ว กด **Uninstall** เพื่อลบ หรือ **Update available** เพื่ออัปเดต
- แท็บ **Catalog** — ค้นหาและกด **Install** (มีหมวด **Featured**)
- ถ้าขึ้น "Can't reach the KODRA skill catalog" แปลว่าโหลดคลังไม่ได้ สกิลในตัวยังใช้ได้ตามปกติ

### สคริปต์ของสกิล

บางสกิลมีสคริปต์ช่วยทำงาน ครั้งแรกที่สคริปต์จะรัน KODRA จะถามคุณก่อน สคริปต์อ่าน/เขียนไฟล์ในแอป
ได้ แต่ใช้อินเทอร์เน็ตหรือรันคำสั่งไม่ได้ ยกเลิกการอนุญาตได้ที่ **Scripts approved · Revoke**

---

## English

**AI teams:** for bigger requests in **Agent** mode, KODRA plans the work and
runs several agents in parallel (Read-only, Writer and Reviewer roles). It
happens automatically, or open the preview's **AI Team** tab and click **Plan this
with a team**. Follow progress in the **AI Team** tab (tasks: In progress, Up next,
Waiting, Done, Failed), stop one agent with **Stop** or all with **Stop team**;
send a message to resume a paused team. Settings → Experiments → AI team:
**Use AI teams for bigger requests** (on), **Agents working at once** (3; lower
it if you hit rate limits), **Install skills automatically** (on). Teams need a
model KODRA calls directly (not Claude Code chats) and use more API credits.

**Skills** are task guides the AI loads while working. Built-in skills cover
auth, email verification, password reset, design system/patterns, local Postgres
and publishing; more come from the
[ko-system/kodra-skills](https://github.com/ko-system/kodra-skills) catalog.
Manage them on the **Skills** page (**Installed** / **Catalog** tabs). Skill
scripts ask for approval on first run; they can read and write your app's files
but cannot use the internet or run commands.
