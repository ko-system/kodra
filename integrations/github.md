---
title: เชื่อมต่อ GitHub
---

[← หน้าแรก](../index.md)

# เชื่อมต่อ GitHub

เชื่อม GitHub เพื่อเก็บโค้ดแอปใน repo ของคุณ ทำงานร่วมกับผู้อื่น และ deploy ผ่าน Vercel
ไปที่แท็บ **Publish** → GitHub

มี 2 วิธี ขึ้นกับว่า KODRA ที่คุณใช้ตั้งค่า GitHub sign-in ไว้หรือไม่

## วิธีที่ 1: Connect to GitHub (device flow)

ถ้าเห็นปุ่ม **Connect to GitHub** (เชื่อมต่อกับ GitHub):

1. กดปุ่ม KODRA จะแสดงรหัส 8 ตัว
2. ไปที่ <https://github.com/login/device> แล้วกรอกรหัส
3. กด Authorize — KODRA ขอสิทธิ์ `repo`, `user` และ `workflow`

ถ้าอยากใช้ token แทน กด **Use a personal access token instead**

## วิธีที่ 2: Fine-grained personal access token

ถ้า KODRA แสดงว่า "This KODRA build has no GitHub sign-in app configured…" ให้ใช้ token:

1. กด **Open GitHub token settings** (หรือไปที่
   <https://github.com/settings/personal-access-tokens/new>)
   — เมนูเต็ม: Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token
2. ตั้งชื่อและวันหมดอายุ
3. **Repository access:** เลือก **All repositories** (เพื่อให้ KODRA สร้าง repo ใหม่ได้)
4. **Repository permissions:**

   | Permission | ระดับ | ใช้ทำอะไร |
   |---|---|---|
   | Contents | Read and write | push/pull โค้ด |
   | Administration | Read and write | สร้าง repo, จัดการ collaborator และ deploy key |
   | Metadata | Read-only | (บังคับ) |
   | Workflows | Read and write | เฉพาะเมื่อแอปมีไฟล์ GitHub Actions (`.github/workflows/`) |

5. **Account permissions (ไม่บังคับ):** Email addresses: Read-only — ให้ commit ใช้อีเมล GitHub ของคุณ
6. ถ้าจะใช้กับ repo ของ **organization** ให้เลือก organization นั้นเป็น **Resource owner**
   (organization อาจต้องอนุมัติ token ก่อน)
7. กด Generate token คัดลอก (ขึ้นต้นด้วย `github_pat_`) วางในช่อง
   **GitHub personal access token** แล้วกด **Connect** จะเห็น "Connected to GitHub as …"

token แบบ classic (`ghp_…`) ใช้ได้ถ้ามี scope `repo` (และ `workflow` ถ้าแอปมี GitHub Actions)

> ห้ามวาง token ในแชตกับ AI หรือใน GitHub issue

## แก้ปัญหา {#troubleshooting}

เมื่อการทำงานกับ GitHub ล้มเหลว (sync/push, rebase, force push, เชื่อม/ยกเลิกการเชื่อม repo)
KODRA จะแสดง **GitHub operation failed** พร้อมลิงก์มาที่หน้านี้ error ยาว ๆ กดคัดลอกได้

| อาการ | วิธีแก้ |
|---|---|
| **Reconnect your GitHub account** | แอปผูก repo ไว้ แต่ไม่มี token ที่บันทึก (เช่น ย้ายเครื่อง) ให้เชื่อม GitHub ใหม่ |
| 401 / Bad credentials | token หมดอายุหรือถูกยกเลิก สร้าง token ใหม่แล้วเชื่อมใหม่ |
| 403 / Resource not accessible by personal access token | token ขาดสิทธิ์ ตรวจ Contents และ Administration = Read and write และ repo อยู่ใน Repository access |
| push ไฟล์ใน `.github/workflows/` ไม่ได้ | เพิ่ม Workflows: Read and write (classic token: scope `workflow`) |
| repo ของ organization ใช้ไม่ได้ | เลือก organization เป็น Resource owner และรอให้ owner อนุมัติ token |
| สร้าง repo ไม่ได้เพราะชื่อซ้ำ | เลือกชื่ออื่น หรือเชื่อมกับ repo ที่มีอยู่แล้ว |
| push ถูกปฏิเสธ (non-fast-forward / rejected) | มี commit ใหม่บน GitHub ที่ยังไม่มีในเครื่อง ให้ sync (pull/rebase) ก่อน แล้วค่อย push ใช้ force push เฉพาะเมื่อแน่ใจว่าจะเขียนทับงานบน GitHub |
| มี conflict หลัง rebase/pull | ให้ AI ช่วยแก้ conflict หรือแก้ในไฟล์เอง แล้ว sync ใหม่ |
| "KODRA couldn't check the repository." | ตรวจอินเทอร์เน็ตและสิทธิ์ token แล้วลองใหม่ |

ยังไม่หาย: [แจ้งปัญหา](../report-a-problem.md) พร้อม error ที่คัดลอกไว้ (ลบ token หรือ URL ที่มี token ออกก่อน)

---

## English

Publish tab → GitHub.

- **Device flow** (when the build has a GitHub sign-in app): **Connect to
  GitHub**, enter the 8-character code at <https://github.com/login/device>, and
  authorize (`repo`, `user`, `workflow`). **Use a personal access token instead**
  switches to a token.
- **Fine-grained token** (when "This KODRA build has no GitHub sign-in app
  configured"): **Open GitHub token settings** → Repository access **All
  repositories** → permissions **Contents: Read and write**, **Administration: Read
  and write**, **Metadata: Read-only**, **Workflows: Read and write** (only for apps
  with GitHub Actions); optional Account → Email addresses: Read-only. For org
  repos pick the org as **Resource owner**. Paste the `github_pat_…` token →
  **Connect**. Classic `ghp_` tokens need `repo` (+ `workflow`).

**Troubleshooting:** "Reconnect your GitHub account" → connect again; 401 →
token expired/revoked; 403 → missing permissions or repo not in the token's
access list; workflow files rejected → add Workflows permission; org repos →
set Resource owner and get approval; push rejected → sync first, force push only
if you mean to overwrite GitHub; conflicts → resolve then sync. Never post
tokens in chats or issues.
