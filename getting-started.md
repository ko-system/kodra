---
title: เริ่มต้นใช้งาน
---

[← หน้าแรก](index.md)

# เริ่มต้นใช้งาน KODRA

## 1. เปิด KODRA

**Desktop:** ติดตั้งโปรแกรม KODRA ที่ได้รับจากผู้ดูแลแล้วเปิดใช้งานได้เลย ไม่ต้องสมัครบัญชี
แอปที่สร้างจะเก็บไว้ในโฟลเดอร์ `~/kodra-apps` ในเครื่องของคุณ

**Web:** เปิดเว็บ KODRA (เช่น `https://app.wt.in.th`) แล้วเข้าสู่ระบบด้วย **Username** และ
**Password** ที่ผู้ดูแลสร้างให้ หรือตั้งรหัสผ่านเองจากลิงก์คำเชิญ (ไม่มีการสมัครเอง ดู
[คำเชิญและคอนโซลผู้ดูแล](guides/web-admin.md)) ติ๊ก "Remember my username on this device"
ได้ถ้าเป็นเครื่องส่วนตัว ระบบจะออกจากระบบอัตโนมัติเมื่อไม่ได้ใช้งาน 12 ชั่วโมง หรือครบ 7 วัน
ถ้าใส่รหัสผิดหลายครั้งติดกัน ระบบจะให้รอสักครู่ก่อนลองใหม่

## 2. ใส่ API key ของผู้ให้บริการ AI (BYOK)

KODRA ไม่มีโควตา AI ให้ฟรี คุณต้องใช้ API key ของคุณเอง

1. ไปที่ **Settings → Model Providers** (ผู้ให้บริการโมเดล AI)
2. เลือกผู้ให้บริการ เช่น
   - **Google (Gemini)** — มี free tier สร้าง key ที่ <https://aistudio.google.com/api-keys>
   - **OpenRouter** — มีโมเดลฟรีบางตัว สร้าง key ที่ <https://openrouter.ai/settings/keys>
   - **OpenAI** — <https://platform.openai.com/api-keys>
   - **Anthropic (Claude)** — <https://console.anthropic.com/settings/keys>
   - อื่น ๆ: Google Vertex AI, Azure OpenAI, xAI, AWS Bedrock, MiniMax, โมเดลในเครื่อง (Ollama, LM Studio)
     หรือ **Add custom provider** สำหรับ API ที่เข้ากันได้กับ OpenAI
3. วาง key ในช่อง **Set … API Key** แล้วกด **Save Key** (หรือ **Paste & Save**) จากนั้นกด
   **Test Key** เพื่อตรวจว่าใช้ได้

ค่าใช้จ่ายการเรียก AI จะคิดกับบัญชีผู้ให้บริการของคุณโดยตรง (ดูยอดโดยประมาณและตั้งขีดจำกัดได้ ดู
[ค่าใช้จ่าย AI](guides/spend-and-routing.md)) อย่าแชร์ key ให้ผู้อื่น และอย่าวาง key ในแชตหรือใน issue

> ถ้ามีแพ็กเกจ ChatGPT หรือ Claude อยู่แล้ว ในเมนูเลือกโมเดลมีหัวข้อ **Subscription**
> ให้เชื่อม **ChatGPT subscription** ได้ ส่วน **Claude Code subscription** ยังเป็นฟีเจอร์ทดลอง
> ต้องเปิดที่ **Settings → Experiments** ก่อน และต้องมี Claude Code CLI ในเครื่อง

## 3. สร้างแอปแรก

1. ที่หน้าแรก พิมพ์สิ่งที่อยากได้ในช่อง "Ask KODRA to build…" เช่น
   *"ทำเว็บจองคิวร้านตัดผม มีหน้าเลือกวันเวลา และหน้าแอดมินดูรายการจอง"*
2. ถ้าเปิด **App Blueprint** ไว้ (Settings → Workflow) KODRA จะเสนอแผนแอปและ
   [ทิศทางการออกแบบ](guides/design-directions.md) ให้เลือกก่อนเริ่มเขียนโค้ด
3. ระหว่างสร้าง จะเห็นตัวอย่างแอปในแผง **Preview** ด้านขวา แผงนี้ยังมีแท็บ
   **Code**, **Publish**, **Configure**, **Brand**, **Features**, **Problems**, **Security**, **Tests**
   และ **AI Team** (ดู [แบรนด์และการออกแบบ](guides/brand-and-design.md) และ
   [ตรวจคุณภาพ](guides/quality-checks.md))
4. แชตต่อเพื่อแก้ไข เช่น *"เปลี่ยนสีหลักเป็นเขียว"* หรือ *"เพิ่มหน้าเข้าสู่ระบบ"*

อยากเริ่มจากโครงที่ต่างออกไป เลือกเทมเพลตเริ่มต้นได้ที่หน้า **Templates**
(React/Vite เป็นค่าเริ่มต้น, Next.js, Fullstack Vite + Nitro, [Portal](templates/portal.md))
หรือกด **Import App** เพื่อนำเข้าโฟลเดอร์ ไฟล์ .zip หรือ repo จาก GitHub

### ย้อนกลับและประวัติเวอร์ชัน

- ใต้ข้อความล่าสุดของ AI มีปุ่ม **Undo** (ย้อนกลับ) และ **Retry**
- ที่หัวแชตจะแสดง "Version N" กดเพื่อเปิด **Version History** เลือกดูเวอร์ชันเก่า
  แล้วกด **Restore to this version** เพื่อกลับไปใช้เวอร์ชันนั้น

### ถ้า preview ไม่ขึ้น

ในเมนู **More** ของแผง Preview มี **Rebuild** (ติดตั้ง dependencies ใหม่),
**Clear Cache** และ **Recreate Sandbox** ลองตามลำดับ ดูเพิ่มที่ [FAQ](faq.md)

## 4. โหมดแชต

เปลี่ยนโหมดได้ที่ปุ่มเลือกโหมดใต้ช่องพิมพ์ (คีย์ลัด ⌘+. / Ctrl+.)

| โหมด | ใช้เมื่อ |
|---|---|
| **Agent** | งานใหญ่หรือดีบัก — AI อ่านไฟล์ รันเครื่องมือ และแก้หลายไฟล์ได้เอง (แนะนำ) |
| **Plan** | อยากออกแบบและตกลงแผนก่อนเริ่มเขียนโค้ด |
| **Build** | สั่งสร้าง/แก้โค้ดตรง ๆ (ใช้กับโมเดลฟรีไม่ได้) |
| **Ask** | ถามคำถามเกี่ยวกับแอป โดยไม่แก้โค้ด |

งานใหญ่ ๆ KODRA อาจตั้ง [ทีม AI](guides/ai-teams-and-skills.md) มาช่วยทำพร้อมกันหลายคน

## 5. เผยแพร่แอป

ในแท็บ **Publish**:
- **GitHub** — ซิงก์โค้ดไป repo ของคุณ (ดู [การเชื่อม GitHub](integrations/github.md))
- **Vercel** — deploy ขึ้น Vercel (ต้องเชื่อม GitHub ก่อน)
- **Web เท่านั้น:** **Publish to …** ตั้งชื่อที่อยู่เว็บ (ตัวพิมพ์เล็ก ตัวเลข และ `-` ยาว 3–40 ตัว)
  ใครมีลิงก์ก็เปิดได้โดยไม่ต้องล็อกอิน และทุกการเปลี่ยนแปลงที่ commit จะขึ้นเว็บอัตโนมัติ
  กด **Unpublish** เพื่อปิด
- ก่อนเผยแพร่จะมีการ์ด **พร้อมเผยแพร่หรือยัง** ตรวจแอปให้ก่อน ดู [ตรวจคุณภาพ](guides/quality-checks.md)

ต้องการฐานข้อมูล ดู [Supabase](integrations/supabase.md) หรือ [Neon](integrations/neon.md)

---

## English

1. **Open KODRA.** Desktop: install the app from your admin; no account needed;
   apps are stored in `~/kodra-apps`. Web: sign in with the username and password
   your admin created or set via an invite link (no self sign-up; sessions end after 12 h idle or 7 days).
2. **Add an AI provider key (BYOK).** Settings → **Model Providers** → pick a
   provider (Google Gemini and OpenRouter have free tiers; also OpenAI,
   Anthropic, Vertex AI, Azure, xAI, Bedrock, MiniMax, Ollama, LM Studio or a
   custom OpenAI-compatible endpoint) → **Save Key** → **Test Key**. A ChatGPT
   subscription can be connected from the model picker's **Subscription** menu.
3. **Create an app.** Type what you want in "Ask KODRA to build…". Watch the
   **Preview** panel, keep chatting to change it, use **Undo** or **Version
   History → Restore to this version** to go back. Pick a default template on
   the **Templates** page or **Import App**.
4. **Chat modes** (⌘/Ctrl + .): **Agent** (bigger tasks, debugging),
   **Plan** (design before you build), **Build** (generate and edit code; not with
   the free model), **Ask** (questions only).
5. **Publish** tab: GitHub, Vercel, and on the web version **Publish to …** a
   public link (every committed change goes live; **Unpublish** to stop). A
   **Ready to publish?** check runs first ([quality checks](guides/quality-checks.md)).

New features: see [What's new](whats-new.md).
