# GitHub Project Standard

มาตรฐานนี้ใช้กับทุกโปรเจกต์ที่ push ขึ้น GitHub ภายใต้บัญชี **Plub-Supanut** — เป้าหมายไม่ใช่แค่ "มีโค้ดอยู่บน GitHub" แต่คือ **เปิด repo แล้วรู้ทันทีว่าคืออะไร ใช้ยังไง เวอร์ชันล่าสุดคืออะไร และไว้ใจผลลัพธ์ได้**

> หลักจำง่าย: **ทุกโปรเจกต์ต้องมี release, ทุก release ต้องมี notes, ทุก repo ต้องมีหน้า README ที่พร้อมให้คนอื่นเปิดดู**

---

## 1. หลักการ 5 ข้อ

1. **Release-first** — โปรเจกต์จะถือว่า publish เสร็จก็ต่อเมื่อมี release อย่างน้อย 1 ครั้ง
2. **Readable by default** — README ต้องอธิบายได้โดยไม่ต้องอ่านโค้ด
3. **Reproducible** — build จาก source ได้ผลเหมือนเดิม และ CI ตรวจทุกครั้ง
4. **Traceable** — ทุกเวอร์ชันมี tag, changelog, release notes และ artifact
5. **Safe to share** — ไม่มี secret, ไม่มี patient data, ระบุ license/attribution ให้ชัด

---

## 2. Definition of Done — ทุก repo ต้องมี

| หมวด | สิ่งที่ต้องมี | เกณฑ์ผ่าน |
| --- | --- | --- |
| Metadata | Description | สั้น ชัด ว่าทำอะไร ภายในประมาณ 160 ตัวอักษร |
| Metadata | Topics | 5–10 topics ที่คนค้นหาได้จริง |
| Metadata | Social preview (public repo) | รูป 1280×640 อัปโหลดใน Settings → Social preview; private repo ใหม่จะไม่เห็นเมนูนี้ |
| หน้า repo | README | มี banner, badges, quick start, features, screenshots, license/attribution |
| Release | อย่างน้อย 1 release | `v1.0.0` สำหรับงานที่ใช้ได้จริง หรือ `v0.1.0` pre-release |
| Release | Release notes | เขียนมือใน `docs/releases/vX.Y.Z.md` ไม่ใช้ auto notes เปล่า ๆ |
| Release | Artifact | แนบไฟล์ที่พร้อมใช้ (HTML, zip, binary, package) เมื่อเหมาะสม |
| Versioning | Tag | annotated tag รูปแบบ `vX.Y.Z` |
| History | CHANGELOG | อัปเดตทุก release ตาม Keep a Changelog |
| Quality | CI | build + validation ผ่านบน `main` และ PR |
| Hygiene | `.gitignore`, `.gitattributes`, `.editorconfig` | ไม่มีไฟล์ขยะ/line-ending drift |
| Collaboration | Issue/PR templates | ใช้ได้จริง ไม่เป็น template เปล่า |
| Legal | License decision | ระบุให้ชัดว่าเปิดให้ใช้ต่อหรือไม่ |
| Content | Attribution/disclaimer | ระบุแหล่งที่มาและข้อจำกัดการใช้งาน |

---

## 3. Repo naming & metadata

### ชื่อ repo

- ใช้ `kebab-case` และสื่อสิ่งที่โปรเจกต์ทำ เช่น `ecg-field-guide`, `thai-note-toolkit`
- หลีกเลี่ยงชื่อกว้าง ๆ เช่น `project1`, `test`, `my-app`
- ถ้าเป็นชุดงานเดียวกัน ให้ใช้ prefix เดียวกัน เช่น `med-*`

### Description

รูปแบบที่แนะนำ:

```text
<สิ่งที่มันทำ> — <จุดเด่น 1–2 อย่าง> · <stack/บริบท ถ้าจำเป็น>
```

ตัวอย่าง:

```text
Interactive ECG field guide — quick criteria review, 9-lesson course, offline-ready single HTML.
```

### Topics

ใส่ 5–10 ตัวที่คนจะใช้ค้นหา เช่น:

```text
ecg, electrocardiogram, cardiology, medical-education,
clinical-skills, interactive-learning, html, javascript, thai, study-notes
```

### Social preview

- ขนาด **1280×640 px**, ไฟล์ PNG/JPG/GIF **ไม่เกิน 1 MB**
- ใช้ชื่อโปรเจกต์ + tagline + ภาพประกอบหนึ่งชิ้น
- ตำแหน่งปกติ: **Settings → General → Social preview → Edit → Upload an image...**
- เก็บไฟล์ไว้ใน `assets/social-preview.png` เพื่อให้แก้ไข/อัปโหลดใหม่ได้ง่าย

> **ข้อจำกัดของ GitHub:** อัปโหลดได้กับ **public repo** หรือ **private repo ที่เคยมีภาพ social preview อยู่แล้ว** เท่านั้น และภาพจะถูกแชร์ได้จาก public repo เท่านั้น ถ้าเป็น private repo ใหม่ เมนู Social preview อาจไม่แสดง — ต้องเปลี่ยนเป็น public ก่อน

### Tabs

- เปิด Issues ถ้ามีคนแจ้งปัญหา/แก้เนื้อหา
- ปิด Projects/Wiki ถ้าไม่ได้ใช้จริง
- เปิด Discussions เฉพาะเมื่อมีชุมชนเข้ามาคุยจริง

---

## 4. README blueprint

README ที่ดีควรเรียงตามนี้:

| ลำดับ | ส่วน | ต้องมีอะไร |
| --- | --- | --- |
| 1 | Banner | ภาพ-wide + ชื่อโปรเจกต์ + tagline 1 บรรทัด |
| 2 | Badges | Release, CI, platform/offline, ภาษาหรือ stack |
| 3 | Quick links | Download, demo, changelog, standard |
| 4 | Overview | ปัญหาที่แก้ / ทำอะไร / ใครใช้ |
| 5 | Quick start | 3 ขั้นหรือน้อยกว่า |
| 6 | Features | bullet 6–10 ข้อที่ผู้ใช้เห็นประโยชน์ |
| 7 | Screenshots | 1–3 ภาพ พร้อม alt text |
| 8 | Controls/Usage | shortcut หรือคำสั่งสำคัญ |
| 9 | Project structure | tree สั้น ๆ |
| 10 | Development | build/test commands |
| 11 | Release policy | link มาที่มาตรฐานนี้ |
| 12 | Attribution + disclaimer | แหล่งที่มาและข้อจำกัด |
| 13 | License | ระบุชัด |

หลักสำคัญ:

- อย่าเริ่มด้วยประวัติยาว ๆ ของผู้เขียน
- ภาพต้องมี `alt`
- ปุ่ม/ลิงก์ต้องพาไปที่ release หรือ demo จริง
- หลีกเลี่ยง badge ที่ไม่ได้ใช้งาน (เช่น badge license ถ้าไม่มี license)

---

## 5. Versioning & release policy

### Semantic Versioning

| เปลี่ยนอะไร | ตัวอย่าง | Version |
| --- | --- | --- |
| แก้บั๊ก/แก้คำผิด/ปรับ typography | fix | `PATCH` → `1.0.1` |
| เพิ่ม feature ที่เข้ากับของเดิม | feat | `MINOR` → `1.1.0` |
| เปลี่ยน behavior/โครงสร้างที่ผู้ใช้ต้องปรับตาม | breaking | `MAJOR` → `2.0.0` |
| ยังไม่พร้อมใช้จริง | beta/RC | `0.x.y` หรือ `-rc.1` |

### กฎที่ห้ามละเลย

1. **ทุกโปรเจกต์ต้องมี release อย่างน้อย 1 ครั้ง** ก่อนถือว่า publish เสร็จ
2. **ทุกการเปลี่ยนแปลงที่ผู้ใช้เห็นต้องออก release ใหม่** ไม่ปล่อยค้างไว้ใน `main` เฉย ๆ
3. **ทุก tag ต้องเป็น annotated tag** และขึ้นต้นด้วย `v`
4. **ทุก release ต้องมี release notes ที่เขียนด้วยคน** ไม่ใช่ auto-generated ล้วน
5. **ทุก release ต้องมี artifact** ถ้าเป็น app/HTML ให้แนบไฟล์ที่พร้อมเปิด
6. **ห้าม release ว่าง** ถ้าไม่มีอะไรเปลี่ยน ให้ไม่ต้อง release
7. **`latest` ต้องชี้ตัวล่าสุดที่เสถียร** ส่วน beta ให้ทำเป็น pre-release
8. **Release notes ต้องมี**: what changed, who it affects, how to use/upgrade, known issues
9. **Docs/CI/tooling-only changes** ที่ไม่กระทบ artifact ไม่ต้อง bump release แต่ต้องผ่าน CI และใช้ commit type `docs:`, `ci:`, หรือ `chore:` ให้ชัด

### Release checklist

- [ ] อัปเดต `CHANGELOG.md` แล้ว
- [ ] เขียน `docs/releases/vX.Y.Z.md` แล้ว (เริ่มจาก [`docs/releases/TEMPLATE.md`](releases/TEMPLATE.md))
- [ ] `python build.py` แล้ว committed output ไม่ stale
- [ ] `python scripts/check.py` ผ่าน
- [ ] ตรวจหน้าเว็บจริง (desktop + mobile) ถ้ามี UI change
- [ ] commit บน `main` เรียบร้อย
- [ ] tag `vX.Y.Z` เป็น annotated tag
- [ ] push `main` และ tag
- [ ] `gh release create` พร้อม notes + artifact
- [ ] ตรวจ Release page ว่าแสดง notes/asset ถูก
- [ ] ตรวจว่า README badge/changelog ชี้เวอร์ชันล่าสุดถูก

---

## 6. Commit, branch และ PR

### Commit message

ใช้ [Conventional Commits](https://www.conventionalcommits.org/):

```text
feat: add QTc calculator
fix: prevent Thai tone marks from overlapping
docs: add release checklist
ci: validate generated HTML
chore(repo): add issue templates
```

### Branch

- `main` ต้องพร้อม release เสมอ
- งานใหม่ใช้ branch เช่น `feat/qtc-calculator`, `fix/thai-leading`
- งานใหญ่เปิด PR เพื่อให้อ่าน diff และเก็บประวัติ
- เปิด **squash merge** และ **delete branch on merge** ใน repo settings

### PR checklist

- [ ] build ผ่าน
- [ ] tests/check ผ่าน
- [ ] อัปเดต docs/changelog ถ้าจำเป็น
- [ ] แนบ screenshot ก่อน/หลัง สำหรับ UI change
- [ ] ไม่มี secret หรือ patient data
- [ ] content change มีแหล่งอ้างอิง

---

## 7. Repo page ให้สวยและดูมืออาชีพ

- [ ] Description ชัดเจน
- [ ] Topics ครบ
- [ ] Social preview 1280×640 (เฉพาะ public หรือ private ที่เคยมีภาพอยู่แล้ว)
- [ ] README มี banner + badges + screenshot
- [ ] Release ล่าสุดแสดงบนหน้า repo
- [ ] CHANGELOG และ license/notice ชัด
- [ ] Issue/PR templates พร้อมใช้
- [ ] ปิด tab ที่ไม่ได้ใช้
- [ ] Pin repo ที่สำคัญไว้บนโปรไฟล์
- [ ] ตั้ง `main` เป็น default branch

> **Private repo note:** dynamic Shields.io/Actions badges มักไม่แสดงผลใน private repo เพราะ service ภายนอกอ่าน repo ไม่ได้ ให้ใช้ static badges หรือทำ repo เป็น public ก่อนติด badge แบบ dynamic

---

## 8. งานที่มีเนื้อหา medical/education

เพิ่มกฎเหล่านี้:

- ระบุ **source, ผู้สอน/ผู้เขียน, วันที่** ให้ชัด
- ใส่ **disclaimer** ว่าไม่ใช่การวินิจฉัยหรือแทน clinical judgement
- ระบุว่า ECG trace/ภาพเป็น **schematic** ถ้าไม่ได้มาจากผู้ป่วยจริง
- ห้ามใส่ชื่อผู้ป่วย, HN, รูปที่มี identifiable data หรือข้อมูลที่ใช้ระบุตัวตนได้
- เนื้อหาที่กระทบ clinical decision ควรมีคนตรวจซ้ำก่อน publish
- ระบุเวอร์ชันของเนื้อหา เช่น `content reviewed: 2026-11-02`

---

## 9. Automation ที่ใช้ใน repo นี้

### CI

`.github/workflows/ci.yml` ทำ:

1. checkout
2. setup Python
3. `python build.py`
4. ตรวจว่า generated HTML ไม่ stale
5. `python scripts/check.py`

### Publish

```powershell
# ต้องอยู่ใน working tree ที่ clean และอยู่บน main
pwsh -File scripts/publish.ps1 -Version 1.0.0
```

สคริปต์จะ:

1. ตรวจ version และ tag ซ้ำ
2. ตรวจ `CHANGELOG.md` และ release notes
3. build + check
4. ตรวจว่า generated files ถูก commit แล้ว
5. push `main`
6. สร้าง annotated tag
7. push tag
8. `gh release create` พร้อมแนบ `ecg-field-guide.html`

### Manual fallback

ถ้าไม่ใช้ script:

```powershell
python build.py
python scripts/check.py
git add .
git commit -m "chore(release): vX.Y.Z"
git push origin main
git tag -a vX.Y.Z -m "Release vX.Y.Z"
git push origin vX.Y.Z
gh release create vX.Y.Z ecg-field-guide.html#Standalone-HTML `
  --title "ECG Field Guide vX.Y.Z" `
  --notes-file "docs/releases/vX.Y.Z.md" `
  --verify-tag
```

---

## 10. Checklist สำหรับโปรเจกต์ใหม่

```powershell
# 1) สร้าง repo ใหม่
gh repo create my-project --private --source=. --remote=origin --push

# 2) ใส่ metadata
gh repo edit --description "..." `
  --add-topic "..." --add-topic "..."

# 3) ตั้งค่า merge
gh api -X PATCH repos/Plub-Supanut/my-project `
  -F allow_squash_merge=true `
  -F allow_merge_commit=false `
  -F allow_rebase_merge=true `
  -F delete_branch_on_merge=true
```

จากนั้น:

- [ ] README ตาม blueprint
- [ ] `.gitignore`, `.gitattributes`, `.editorconfig`
- [ ] CI
- [ ] CHANGELOG
- [ ] issue/PR templates
- [ ] license decision
- [ ] release notes
- [ ] tag + release
- [ ] social preview

---

## 11. นิยามของ "เสร็จ"

โปรเจกต์จะเรียกว่า **publish แล้ว** เมื่อ:

1. มี repo ที่มี description/topics/social preview
2. มี README ที่คนอื่นอ่านแล้วใช้งานได้
3. มี CI ที่ผ่าน
4. มี tag และ GitHub Release ที่มี notes + artifact
5. มี changelog
6. มี attribution/disclaimer/license decision
7. ไม่มี secret หรือข้อมูลส่วนบุคคล

ถ้าข้อใดข้อหนึ่งยังไม่มี ให้ถือว่ายังไม่เสร็จ
