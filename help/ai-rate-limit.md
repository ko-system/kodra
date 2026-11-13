---
title: AI ตอบว่าเกินโควตา (rate limit)
---

[← หน้าแรก](../index.md) · [FAQ](../faq.md)

# AI ตอบว่าเกินโควตา (rate limit)

KODRA ใช้ API key ของคุณ (BYOK) ดังนั้นขีดจำกัดเป็นของ**บัญชีผู้ให้บริการ AI ของคุณ** ไม่ใช่ของ KODRA

## อาการ

- error มีรหัส **429**, คำว่า *rate limit*, *quota*, **"Resource has been exhausted"**
  (Google Gemini) หรือ **"Provider returned error"** (OpenRouter)
- เกิดบ่อยกับ free tier ซึ่งจำกัดจำนวนคำขอต่อนาที / ต่อวัน

## วิธีแก้

1. **รอ 1–2 นาที** แล้วส่งใหม่ — ขีดจำกัดต่อนาทีจะรีเซ็ตเอง
2. **เปลี่ยนโมเดลหรือผู้ให้บริการ** จากเมนูเลือกโมเดล เช่น สลับจาก Gemini ไป OpenRouter หรือกลับกัน
3. **ลดงานที่ทำพร้อมกัน** — [ทีม AI](../guides/ai-teams-and-skills.md) เรียกโมเดลหลายตัวพร้อมกัน
   ลด **Agents working at once** ใน Settings → Experiments หรือปิด
   **Use AI teams for bigger requests** ชั่วคราว
4. **เพิ่มโควตา** — เปิด billing / เติมเครดิตกับผู้ให้บริการ (free tier มีโควตาต่ำมาก)
   - Google: <https://aistudio.google.com> → ดูโควตาและเปิด billing ของโปรเจกต์
   - OpenRouter: เติมเครดิตที่ <https://openrouter.ai/settings/credits>
   - OpenAI / Anthropic: ขีดจำกัดจะสูงขึ้นตาม tier การใช้จ่ายของบัญชี
5. ถ้าเป็นโควตารายวัน ต้องรอวันถัดไป (ตามเวลาของผู้ให้บริการ)

---

## English

KODRA uses your own provider key, so rate limits belong to **your provider
account**. Symptoms: HTTP **429**, "rate limit", "quota", **"Resource has been
exhausted"** (Gemini) or **"Provider returned error"** (OpenRouter), most often
on free tiers. Fixes: wait a minute and retry; switch model or provider; lower
**Agents working at once** (Settings → Experiments) or turn off AI teams for a
while, since teams call the model in parallel; enable billing / add credits with
your provider; daily quotas reset the next day.
