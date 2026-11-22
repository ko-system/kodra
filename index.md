---
title: KODRA
---

# KODRA — สร้างแอปด้วย AI

KODRA คือเครื่องมือสร้างเว็บแอปด้วย AI: พิมพ์บอกว่าอยากได้แอปแบบไหน แล้ว AI จะเขียนโค้ด
แสดงตัวอย่าง (preview) และแก้ไขตามที่คุณสั่งต่อได้เรื่อย ๆ โค้ดทั้งหมดเป็นของคุณ
และใช้ API key ของผู้ให้บริการ AI ของคุณเอง (BYOK — Bring Your Own Key)

KODRA พัฒนาต่อยอดจากโปรเจกต์โอเพนซอร์ส [Dyad](https://github.com/dyad-sh/dyad)

## ใช้งานได้ 2 แบบ

| | Desktop | Web |
|---|---|---|
| ติดตั้ง | ติดตั้งโปรแกรมบน macOS / Windows / Linux | เปิดผ่านเบราว์เซอร์ ไม่ต้องติดตั้ง |
| บัญชี | ไม่ต้องสมัคร | เข้าสู่ระบบด้วยบัญชีที่ผู้ดูแลสร้างให้ |
| โค้ดของแอป | เก็บในเครื่องคุณ (ค่าเริ่มต้น `~/kodra-apps`) | เก็บบนเซิร์ฟเวอร์ของ KODRA |
| เผยแพร่แอป | GitHub, Vercel | GitHub, Vercel และปุ่ม **Publish** เป็นลิงก์สาธารณะ |
| แอปมือถือ (Capacitor) | ได้ (ต้องมี Xcode / Android Studio) | ไม่รองรับการเปิด Xcode / Android Studio |

## คู่มือ

**ใหม่**
- [มีอะไรใหม่ (2026-11-23)](whats-new.md)

**เริ่มต้น**
- [เริ่มต้นใช้งาน](getting-started.md) — เข้าสู่ระบบ, ใส่ API key, สร้างแอปแรก, โหมดแชต
- [คำถามที่พบบ่อย (FAQ)](faq.md)
- [AI ตอบว่าเกินโควตา / rate limit](help/ai-rate-limit.md)

**การเชื่อมต่อบริการ**
- [Supabase](integrations/supabase.md)
- [Neon (Postgres)](integrations/neon.md)
- [GitHub](integrations/github.md)
- [ค้นหาเว็บและสร้างรูปภาพด้วย key ของคุณ](guides/byok-tools.md)
- [บริการไทย: LINE, พร้อมเพย์, Omise](integrations/thai-services.md)

**ฟีเจอร์**
- [ค่าใช้จ่าย AI และ Smart routing](guides/spend-and-routing.md)
- [แบรนด์และการออกแบบ (Brand Studio, บล็อก, โหมดออกแบบ)](guides/brand-and-design.md)
- [ตรวจคุณภาพและทดสอบแอป](guides/quality-checks.md)
- [งานตามกำหนดเวลา (Routines)](guides/routines.md)
- [ข้อผิดพลาดบนเว็บจริง และสถานะเว็บไซต์จริง](guides/production-monitoring.md)
- [แอปติดตั้งได้ (PWA)](guides/pwa.md)
- [เวอร์ชันเว็บ: คำเชิญ และคอนโซลผู้ดูแล](guides/web-admin.md)
- [ทีม AI และสกิล](guides/ai-teams-and-skills.md)
- [ทิศทางการออกแบบ (Design directions)](guides/design-directions.md)
- [ตรวจความปลอดภัย (Security Review)](guides/security-review.md)
- [แอปมือถือ (Capacitor)](guides/mobile-app.md)
- [เทมเพลต Portal](templates/portal.md)

**อัปเกรดและกู้คืน**
- [อัปเกรด: Select component](upgrades/select-component.md)
- [อัปเกรด: ย้ายไป pnpm 11](upgrades/pnpm-migration.md)
- [ย้ายข้อมูลและกู้คืนการตั้งค่า](guides/migrate-restore.md)

**แจ้งปัญหา**
- [วิธีแจ้งปัญหาหรือขอฟีเจอร์](report-a-problem.md)

---

## English

KODRA is an AI app builder: describe the app you want, and the AI writes the
code, shows a live preview and keeps editing it as you chat. You own the code
and use your own AI provider API keys (BYOK). KODRA is based on the open-source
project [Dyad](https://github.com/dyad-sh/dyad).

It comes as a **desktop app** (macOS / Windows / Linux; apps live in
`~/kodra-apps` on your machine) and a **web version** (sign in with an account
your admin creates; apps live on the KODRA server and can be published to a
public link). Start with [Getting started](getting-started.md) and see
[What's new](whats-new.md) for the latest features; every page
above has a short English section at the end.

Found a bug? See [Reporting a problem](report-a-problem.md).
