# KODRA

**คู่มือการใช้งานและช่องทางแจ้งปัญหาของ KODRA** — เครื่องมือสร้างแอปด้วย AI (desktop และ web)

**KODRA user documentation and public issue tracker** — the AI app builder (desktop and web).

📖 **คู่มือ / Docs:** <https://ko-system.github.io/kodra/>

## แจ้งปัญหา / Report a problem

- ในแอป: **Help → Report a Bug** แอปจะกรอกเวอร์ชันและข้อมูลระบบให้อัตโนมัติ
- หรือเปิด [issue ใหม่](https://github.com/ko-system/kodra/issues/new/choose) แล้วเลือก
  **Bug report** หรือ **Feature request**
- issue เป็น **ข้อมูลสาธารณะ** ห้ามใส่ API key, token, รหัสผ่าน หรือข้อมูลส่วนตัว
  และอย่าแนบไฟล์ debug bundle (`kodra-session-*.json`) ใน issue — ส่งให้ผู้ดูแลแบบส่วนตัว
- ช่องโหว่ด้านความปลอดภัย: ใช้
  [Report a vulnerability](https://github.com/ko-system/kodra/security/advisories/new)

---

- In the app: **Help → Report a Bug** pre-fills your version and system info.
- Or open a [new issue](https://github.com/ko-system/kodra/issues/new/choose) and
  pick **Bug report** or **Feature request**.
- Issues are **public**: never include API keys, tokens, passwords or personal
  data, and don't attach the `kodra-session-*.json` debug bundle — send it
  privately to your KODRA admin.
- Security vulnerabilities: use
  [Report a vulnerability](https://github.com/ko-system/kodra/security/advisories/new).

See [Reporting a problem](https://ko-system.github.io/kodra/report-a-problem) for details.

## เกี่ยวกับ repo นี้ / About this repository

repo นี้มีเฉพาะคู่มือ (เผยแพร่ด้วย GitHub Pages จาก branch `main`) และ issue tracker
ซอร์สโค้ดของแอปไม่ได้อยู่ที่นี่

This repository holds only the docs (published with GitHub Pages from `main`)
and the issue tracker; the application source is not here.

แก้คู่มือ: แก้ไฟล์ `.md` แล้วเปิด pull request / To edit the docs, change the
Markdown files and open a pull request. Page paths are linked from the app —
don't rename or move existing pages.

Docs licensed under [CC BY 4.0](LICENSE).
