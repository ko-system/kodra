---
title: "อัปเกรด: ย้ายไป pnpm 11"
---

[← หน้าแรก](../index.md)

# อัปเกรด: ย้ายไป pnpm 11

แอปเก่าบางแอปล็อกเวอร์ชัน pnpm เก่า (8 หรือต่ำกว่า) หรือมี `pnpm-lock.yaml` รูปแบบเก่า
ซึ่งอ่าน lockfile ที่ KODRA เขียนไม่ได้ ทำให้ CI, การ deploy หรือเพื่อนร่วมทีมติดตั้งแพ็กเกจไม่ผ่าน

## อาการ

แผง Preview แสดงแถบเตือน **"This app pins an older pnpm that can't read the lockfile KODRA
writes. Migrate to pnpm 11 so CI, deploys, and teammates can install it reliably."**

## อัปเกรดอัตโนมัติ

- กด **Migrate** ในแถบเตือน — KODRA หยุดแอป ย้ายให้ แล้วรีสตาร์ต preview
- หรือไปที่ App Details → **App Upgrades** → **Migrate to pnpm 11** → **Upgrade**

KODRA จะ:
1. ตั้ง `packageManager` ใน `package.json` เป็น pnpm เวอร์ชันที่ KODRA ใช้
2. สร้าง/อัปเดตการตั้งค่าใน `pnpm-workspace.yaml`
3. รัน `pnpm install` เพื่อสร้าง `pnpm-lock.yaml` ใหม่
4. commit `package.json`, `pnpm-lock.yaml` (และ `pnpm-workspace.yaml` ถ้ามีการเปลี่ยน)
   ด้วยข้อความ "migrate to pnpm 11"

## ย้ายเอง

ในโฟลเดอร์แอป (ต้องมี Node.js 22.13 ขึ้นไป):

```sh
npm install -g pnpm@11      # หรือดูวิธีติดตั้งที่ https://pnpm.io/installation
pnpm --version              # จดเวอร์ชันไว้ เช่น 11.x.y
```

1. แก้ `package.json`: `"packageManager": "pnpm@<เวอร์ชันจากข้างบน>"`
2. รัน `pnpm install`
3. commit:

   ```sh
   git add package.json pnpm-lock.yaml pnpm-workspace.yaml
   git commit -m "migrate to pnpm 11"
   ```

| ข้อความ | วิธีแก้ |
|---|---|
| "pnpm is not available … Restart KODRA and try again." | ปิดแล้วเปิด KODRA ใหม่ แล้วลองอีกครั้ง |
| "The migration ran but the changes could not be committed…" | commit `package.json` และ `pnpm-lock.yaml` เอง |

## คำเตือน "Install pnpm 10.16.0 or newer for the strongest protection"

KODRA ตั้ง `minimumReleaseAge: 1440` ใน `pnpm-workspace.yaml` ให้ pnpm ไม่ติดตั้งแพ็กเกจที่เพิ่ง
ออกมาไม่ถึง 24 ชั่วโมง ป้องกันการโจมตีผ่านแพ็กเกจปลอม (supply-chain attack) pnpm รุ่นเก่าทำแบบนี้ไม่ได้

- กด **Install** เพื่อให้ KODRA ติดตั้ง pnpm ใหม่
- ถ้า Node.js เก่ากว่า 22.13.0 จะเห็น "pnpm v11 requires Node.js 22.13.0 or newer…" กด
  **Download Node.js** ติดตั้งแล้วเปิด KODRA ใหม่
- ปิดคำเตือนนี้ได้ที่ Settings → Experiments → **Enable pnpm upgrade warning**

---

## English

Apps that pin pnpm 8 or older, or have an old `pnpm-lock.yaml`, can't read the
lockfile KODRA writes. Click **Migrate** on the preview banner, or App Details →
**App Upgrades** → "Migrate to pnpm 11" → **Upgrade**. KODRA sets
`packageManager` to its pnpm version, ensures `pnpm-workspace.yaml`, runs
`pnpm install` and commits as "migrate to pnpm 11". Manually (Node.js 22.13+):
install pnpm 11, set `"packageManager": "pnpm@<version>"`, run `pnpm install`,
commit `package.json`, `pnpm-lock.yaml` and `pnpm-workspace.yaml`.

The "Install pnpm 10.16.0 or newer" warning is about `minimumReleaseAge: 1440`,
which blocks packages published less than 24 hours ago (supply-chain
protection). Click **Install**, or **Download Node.js** first if Node is older
than 22.13.0. Toggle it under Settings → Experiments → "Enable pnpm upgrade
warning".
