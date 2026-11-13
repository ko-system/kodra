---
title: แอปมือถือ (Capacitor)
---

[← หน้าแรก](../index.md)

# แอปมือถือด้วย Capacitor

KODRA แปลงเว็บแอป (React/Vite) เป็นแอปมือถือ iOS และ Android แบบ hybrid ได้ด้วย
[Capacitor](https://capacitorjs.com) แอปจะยังเป็นโค้ดเว็บชุดเดิม แต่ห่อด้วยโปรเจกต์ Xcode
และ Android Studio เพื่อรันบนมือถือหรือส่งขึ้น App Store / Google Play

> ใช้กับ **KODRA Desktop** — ต้องเปิด Xcode หรือ Android Studio ในเครื่องของคุณเอง

## สิ่งที่ต้องมี

- Node.js **v20 ขึ้นไป**
- iOS: เครื่อง Mac ที่ติดตั้ง **Xcode**
- Android: **Android Studio** (macOS / Windows / Linux)

## อัปเกรดแอปให้เป็นแอปมือถือ {#upgrade-your-app}

1. เปิดหน้ารายละเอียดแอป (App Details) → ส่วน **App Upgrades**
2. ที่รายการ **Upgrade to hybrid mobile app with Capacitor** กด **Upgrade**
   (มีเฉพาะแอป Vite ที่ยังไม่มีไฟล์ `capacitor.config.*`)

KODRA จะทำให้อัตโนมัติ:

```sh
pnpm add @capacitor/core@7.4.4 @capacitor/cli@7.4.4 @capacitor/ios@7.4.4 @capacitor/android@7.4.4
npx cap init "<ชื่อแอป>" "com.example.<ชื่อแอป>" --web-dir=dist
pnpm install --prod=false
npx cap add ios && npx cap add android
```

แล้ว commit ด้วยข้อความ "add Capacitor for mobile app support"
ถ้าอัปเกรดไม่สำเร็จ ให้รันคำสั่งข้างบนเองใน terminal ที่โฟลเดอร์แอป (ถ้าไม่มี pnpm ใช้
`npm install --legacy-peer-deps …` แทน `pnpm add`) แล้ว commit เอง
ควรเปลี่ยน `com.example.<ชื่อแอป>` เป็น bundle id ของคุณเองก่อนส่งขึ้นสโตร์

## เปิดโปรเจกต์ใน Xcode / Android Studio

เมื่อแอปมี Capacitor แล้ว หน้า App Details จะมีการ์ด **Mobile Development**

- **Sync & Open iOS** — build เว็บแอป, `npx cap sync` แล้วเปิด Xcode
- **Sync & Open Android** — build เว็บแอป, `npx cap sync` แล้วเปิด Android Studio

กดทุกครั้งที่แก้โค้ดแล้วอยากเห็นผลบนมือถือ จากนั้นกด Run ใน Xcode / Android Studio

## แก้ปัญหา {#troubleshooting}

ถ้าคำสั่งล้มเหลว จะมีหน้าต่าง "Failed to sync and open … project" พร้อมรายละเอียด กด **Copy Error** เพื่อคัดลอก

| อาการ | วิธีแก้ |
|---|---|
| "Capacitor requires Node.js v20 or higher" | ติดตั้ง Node.js 20+ แล้วเปิด KODRA ใหม่ |
| build เว็บไม่ผ่าน | เปิดแท็บ **Problems** หรือส่ง error ให้ AI แก้ แล้วกด Sync อีกครั้ง |
| เปิด Xcode ไม่ได้ | ติดตั้ง Xcode และรัน `xcode-select --install` / เปิด Xcode หนึ่งครั้งเพื่อยอมรับ license |
| เปิด Android Studio ไม่ได้ | ติดตั้ง Android Studio และ Android SDK ให้เรียบร้อย |
| แอปบนมือถือไม่อัปเดต | กด **Sync & Open** ใหม่ทุกครั้งหลังแก้โค้ด |

ยังไม่หาย: วาง error ที่คัดลอกไว้ในแชตให้ AI ช่วยดู หรือ [แจ้งปัญหา](../report-a-problem.md)

## ขอความช่วยเหลือ {#help}

- คู่มือ Capacitor: <https://capacitorjs.com/docs>
- ส่ง error ให้ AI ในแชตของแอปนั้น (เลือกโหมด **Agent**)
- [แจ้งปัญหา KODRA](../report-a-problem.md)

---

## English

KODRA can wrap a React/Vite app with [Capacitor](https://capacitorjs.com) to
build hybrid iOS and Android apps. Desktop only; you need Node.js 20+, Xcode (on
a Mac) for iOS and/or Android Studio.

- **Upgrade your app:** App Details → **App Upgrades** → "Upgrade to hybrid
  mobile app with Capacitor" → **Upgrade**. It installs `@capacitor/*@7.4.4`, runs
  `npx cap init … --web-dir=dist`, `npx cap add ios && npx cap add android` and
  commits. Run those commands yourself if it fails.
- **Open the native projects:** the **Mobile Development** card →
  **Sync & Open iOS** / **Sync & Open Android** (builds, `npx cap sync`, opens the
  IDE). Re-sync after every change.
- **Troubleshooting:** use **Copy Error** in the failure dialog; install
  Node.js 20+, Xcode or Android Studio; fix build errors first; paste the error
  into the chat or [report a problem](../report-a-problem.md).
