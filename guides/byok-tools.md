---
title: ค้นหาเว็บและสร้างรูปภาพด้วย key ของคุณ
---

[← หน้าแรก](../index.md)

# ค้นหาเว็บและสร้างรูปภาพด้วย key ของคุณ

ตั้งค่าที่ **Settings → AI**

## ค้นหาเว็บ (Web search)

AI จะค้นเว็บได้เมื่อคุณใส่ API key ของบริการค้นหา ถ้าไม่มี key ฟีเจอร์นี้จะปิดอยู่ และ AI จะไม่รู้ว่ามีเครื่องมือนี้

1. สมัครและสร้าง key:
   - **Tavily** (แนะนำ) — <https://app.tavily.com/>
   - **Brave Search** — <https://api-dashboard.search.brave.com/>
2. วาง key ในช่อง **Tavily API key** หรือ **Brave Search API key** แล้วกด **Save**
3. ถ้ามีทั้งสองอย่าง เลือกตัวหลักที่ **Preferred search provider**
   (ถ้าตัวหลักไม่มี key จะใช้อีกตัวแทน)

สถานะจะแสดงว่า "Web search is on, using …" กด **Remove** เพื่อลบ key

> การอ่านหน้าเว็บจากลิงก์ที่คุณให้ หรือการโคลนหน้าเว็บจากลิงก์ ใช้ได้โดยไม่ต้องมี key

## สร้างรูปภาพ (Image generation)

ไม่ต้องตั้งค่าแยก — KODRA ใช้ key ใน **Settings → Model Providers**

- มี **OpenAI** key → ใช้ `gpt-image-1`
- มี **Google (Gemini)** key → ใช้ `imagen-4.0-generate-001`

ถ้ายังไม่มีทั้งสองอย่าง จะเห็น "Add an OpenAI or Google (Gemini) API key under Model Providers to
turn it on." การสร้างรูปคิดค่าใช้จ่ายกับบัญชีผู้ให้บริการของคุณ

---

## English

Settings → **AI**.

- **Web search:** add a **Tavily** (recommended, <https://app.tavily.com/>) or
  **Brave Search** (<https://api-dashboard.search.brave.com/>) API key and click
  **Save**; choose the **Preferred search provider** if you have both. Without a
  key, web search is off and the agent isn't told about it. Reading a page or
  cloning a site from a link works without a key.
- **Image generation:** uses your **OpenAI** key (`gpt-image-1`) or **Google
  (Gemini)** key (`imagen-4.0-generate-001`) from Model Providers; nothing else
  to configure. Usage is billed to your provider account.
