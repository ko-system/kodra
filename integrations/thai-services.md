---
title: เชื่อมต่อบริการไทย (LINE, พร้อมเพย์, Omise)
---

[← หน้าแรก](../index.md)

# เชื่อมต่อบริการไทย: LINE, พร้อมเพย์, Omise

KODRA มีตัวช่วยสำเร็จรูปสำหรับบริการที่ธุรกิจไทยใช้บ่อย:

| บริการ | ใช้ทำอะไร | ต้องมีเซิร์ฟเวอร์ไหม |
|---|---|---|
| **LINE Login และ LIFF** | ล็อกอินด้วย LINE, แอปที่เปิดในแอป LINE | Login ต้องมี / LIFF ไม่ต้อง |
| **LINE Messaging API** | บอท LINE OA ตอบข้อความ แจ้งเตือน | ต้องมี |
| **QR พร้อมเพย์** | แสดง QR ให้ลูกค้าสแกนจ่าย | ไม่ต้อง |
| **Omise (Opn Payments)** | รับบัตรและพร้อมเพย์ ยืนยันการจ่ายอัตโนมัติ | ต้องมี |

ใช้ได้กับแอป Vite, Next.js และ Supabase

## 1. สั่ง AI ในแชต

พิมพ์บอกได้เลย เช่น *"ล็อกอินด้วย LINE"*, *"รับเงินผ่าน PromptPay"*, *"รับบัตรด้วย Omise"*
AI จะเพิ่มโค้ดตัวช่วยที่ทดสอบแล้ว และใช้สกิล **LINE integration** / **Thai payments**
(มาพร้อมแอป ไม่ต้องติดตั้ง) ถ้าแอปยังไม่มีเซิร์ฟเวอร์ AI จะสร้างให้ก่อน

ในแชตจะมีการ์ด **บริการไทย** พร้อมปุ่ม **กรอกคีย์** (Enter keys) — **อย่าวางคีย์ลับในแชต**

## 2. กรอกคีย์

1. เปิดแท็บ **Configure** (ภาษาไทย: **ตั้งค่า**) ในแผง Preview ของแอป
   — คนละที่กับหน้า Settings ของโปรแกรม
2. เปิดการ์ด **การเชื่อมต่อบริการไทย** (Thai integrations)
3. กรอกช่องของบริการที่ใช้ แล้วกดบันทึก

| บริการ | ช่องที่ต้องกรอก | หาได้ที่ |
|---|---|---|
| LINE Login และ LIFF | Channel ID, Channel secret, LIFF ID | LINE Developers Console (LINE Login channel) |
| LINE Messaging API | Channel secret, Channel access token (long-lived) | LINE Developers Console (Messaging API channel) |
| QR พร้อมเพย์ | หมายเลขพร้อมเพย์ (เบอร์มือถือ, เลขประจำตัวประชาชน/เลขผู้เสียภาษี 13 หลัก หรือ e-Wallet ID 15 หลัก), ชื่อบัญชีที่แสดงใต้ QR | — |
| Omise | Public key, Secret key, Webhook secret | Omise dashboard |

ปุ่ม **เปิดคอนโซล** (Open console) พาไปหน้าเว็บของ LINE / Omise ได้เลย

คีย์จะถูกบันทึกในไฟล์ `.env.local` ของแอป (ไม่ถูก commit ขึ้น Git) และมีแต่โค้ดฝั่งเซิร์ฟเวอร์ที่อ่านได้
ถ้าแอปเชื่อม [Supabase](supabase.md) ไว้ ระบบจะซิงก์ไปเป็น secret ของ Edge Function ให้ด้วย

**Omise:** ใช้คีย์ทดสอบ (`pkey_test_` / `skey_test_`) จนกว่าจะพร้อมขายจริง การ์ดจะแสดง
**โหมดทดสอบ** หรือ **โหมดใช้งานจริง** — คีย์โหมดใช้งานจริงจะตัดเงินจริง และ public/secret key
ต้องมาจากโหมดเดียวกัน ยอดชำระผ่านพร้อมเพย์ของ Omise ขั้นต่ำ ฿20

## 3. ตั้ง URL ที่หน้าคอนโซลของผู้ให้บริการ

แทน `<โดเมน>` ด้วยที่อยู่แอปที่เผยแพร่แล้ว (ต้องเป็น https)

- **LINE Login callback:** `https://<โดเมน>/api/auth/line/callback` (ใส่ URL ของเครื่องที่ใช้ทดสอบด้วย)
  หน้าล็อกอินของ LINE เปิดในกรอบพรีวิวไม่ได้ ให้เปิดในแท็บใหม่
- **LINE Messaging webhook:** `https://<โดเมน>/api/line/webhook` แล้วเปิด "Use webhook"
- **Omise webhook:** `https://<โดเมน>/api/omise/webhook` ใน Omise dashboard → Webhooks
  แล้วคัดลอก secret มาใส่ช่อง **Webhook secret**

## สำคัญ: QR พร้อมเพย์ยืนยันการชำระเงินเองไม่ได้

> QR พร้อมเพย์ยืนยันการชำระเงินเองไม่ได้ เพราะแอปไม่ได้รับแจ้งเมื่อมีเงินเข้า
> ควรตรวจยอดในแอปธนาคารก่อนยืนยันคำสั่งซื้อ หรือใช้ Omise หากต้องการยืนยันการชำระเงินอัตโนมัติ

KODRA จึงให้คำสั่งซื้อที่จ่ายด้วย QR อยู่ในสถานะ "รอยืนยัน" จนกว่าร้านจะยืนยันเอง การกด "ชำระแล้ว"
หรืออัปโหลดสลิปอย่างเดียว **ไม่ใช่** หลักฐานการจ่าย (สลิปปลอมได้) ทางเลือก:

- **ยืนยันเอง:** ร้านตรวจยอดในแอปธนาคาร แล้วกดยืนยันในหน้าแอดมิน
- **ยืนยันอัตโนมัติ:** ใช้ Omise (พร้อมเพย์หรือบัตร) ซึ่งแจ้งผลผ่าน webhook
- ถ้าต้องการตรวจสลิปอัตโนมัติ ต้องใช้บริการตรวจสลิปของธนาคาร/ผู้ให้บริการทางฝั่งเซิร์ฟเวอร์

---

## English

KODRA has built-in helpers for **LINE Login & LIFF**, **LINE Messaging API**,
**PromptPay QR** and **Omise (Opn Payments)** (Vite, Next.js and Supabase apps).
Ask in chat ("login with LINE", "accept PromptPay"); the AI adds the code using
the built-in **LINE integration** / **Thai payments** skills. Enter keys in the
app's **Configure** tab (preview panel, not the Settings page) → **Thai
integrations**, or click **Enter keys** on the chat card. Never paste secrets
into chat. Keys are saved in the app's `.env.local` (never committed) and synced
to Supabase Edge Function secrets if the app uses Supabase. Webhook/callback
paths: `/api/auth/line/callback`, `/api/line/webhook`, `/api/omise/webhook`.
Use Omise test keys until you go live (**Test mode** / **Live mode** badge);
Omise PromptPay minimum is ฿20.

**A PromptPay QR can't confirm a payment by itself: the app is never told that
money arrived.** Check your bank app before confirming an order, or use Omise for
automatic confirmation. A "I paid" button or a slip upload alone is not proof.
