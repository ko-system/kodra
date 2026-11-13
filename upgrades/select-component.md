---
title: "อัปเกรด: Select component"
---

[← หน้าแรก](../index.md)

# อัปเกรด: Enable select component to edit

ฟีเจอร์ **select component** ให้คุณคลิกเลือกส่วนต่าง ๆ ในหน้า Preview แล้วสั่ง AI แก้เฉพาะส่วนนั้น
แอปเก่าบางแอปยังไม่รองรับ จึงต้องอัปเกรดหนึ่งครั้ง (เฉพาะแอป Vite + React)

## อัปเกรดอัตโนมัติ

หน้ารายละเอียดแอป (App Details) → **App Upgrades** → **Enable select component to edit** → **Upgrade**

KODRA จะ:
1. เพิ่ม plugin ใน `vite.config.ts` (หรือ `.js`)
2. ติดตั้งแพ็กเกจ `@dyad-sh/react-vite-component-tagger` เป็น dev dependency

ถ้าติดตั้งไม่สำเร็จ KODRA จะคืนค่า `vite.config` เดิมให้ และแสดง **Upgrade Failed** พร้อมลิงก์
**Manual Upgrade Instructions** มาที่หน้านี้

## อัปเกรดเอง

1. ติดตั้งแพ็กเกจในโฟลเดอร์แอป:

   ```sh
   pnpm add -D @dyad-sh/react-vite-component-tagger
   # หรือ
   npm install --save-dev --legacy-peer-deps @dyad-sh/react-vite-component-tagger
   ```

2. แก้ `vite.config.ts` — เพิ่ม import ต่อจาก import บรรทัดสุดท้าย และใส่ plugin เป็นตัวแรกใน `plugins`:

   ```ts
   import { defineConfig } from "vite";
   import react from "@vitejs/plugin-react";
   import dyadComponentTagger from "@dyad-sh/react-vite-component-tagger";

   export default defineConfig({
     plugins: [dyadComponentTagger(), react()],
   });
   ```

3. commit การเปลี่ยนแปลง แล้วกด **Rebuild** ในแผง Preview

ถ้าเห็น "Could not find 'plugins: [' in vite.config.ts. Manual installation required."
แปลว่า config ของคุณเขียนต่างจากรูปแบบปกติ ให้ทำตามขั้นตอนนี้เอง

---

## English

**Select component** lets you click an element in the preview and ask the AI to
edit just that part. Older Vite + React apps need a one-time upgrade: App Details
→ **App Upgrades** → "Enable select component to edit" → **Upgrade**. Manually:
install `@dyad-sh/react-vite-component-tagger` as a dev dependency
(`pnpm add -D …` or `npm install --save-dev --legacy-peer-deps …`), add
`import dyadComponentTagger from "@dyad-sh/react-vite-component-tagger";` after
the last import in `vite.config.ts`, put `dyadComponentTagger()` first in
`plugins: [...]`, commit and **Rebuild**.
