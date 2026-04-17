---
name: codeblock-tabs
description: >
  Format output sebagai code block dengan tab indentation (bukan tree characters seperti ├ └ │).
  Gunakan skill ini SETIAP KALI user meminta:
  - "pakai tabs", "pakai tab", "format tabs", "dengan tab"
  - flow tree, sitemap, struktur halaman, user flow
  - hierarki konten yang butuh indentasi visual
  - "tree tapi pakai tab" atau "tanpa simbol tree"
  Output harus selalu dalam ```tree code block dengan tab indentation murni.
  JANGAN pakai ├ └ │ ─ atau karakter tree unicode lainnya kecuali diminta eksplisit.
---

# Codeblock Tabs Skill

Format hierarki konten menggunakan **tab indentation** di dalam code block.
Bukan tree characters. Bukan bullet. Bukan dash. Tab murni.

---

## Output Format

Selalu wrap dalam code block dengan language tag `tree`:

\`\`\`tree
Parent
	Child level 1
		Child level 2
			Child level 3
\`\`\`

---

## Rules

1. **Gunakan TAB (\t) untuk indentasi** — bukan spasi, bukan ├ └ │
2. **Wrap dalam ```tree code block** — selalu, tanpa pengecualian
3. **Tiap level = 1 tab tambahan** dari parent-nya
4. **Tidak ada karakter dekorasi** — tidak ada -, *, •, ├, └, │, ─
5. **Teks apa adanya** — label boleh pakai [ ] untuk button, → untuk arah, : untuk keterangan
6. **Boleh pakai komentar inline** dengan ← setelah item untuk anotasi singkat
7. **Gunakan baris kosong** untuk memisahkan branch/group baru agar mudah dibaca

---

## Branch Separator

Gunakan **1 baris kosong** antara tiap branch level 1 untuk visual grouping:

\`\`\`tree
Root

	Branch A
		item 1
		item 2

	Branch B
		item 1
		item 2

	Branch C
		item 1
\`\`\`

---

## Contoh Benar

\`\`\`tree
PakCli Landing Page

	hero
		btn mulai jelajahi

	5 bidang ilmu
		IT
		IPA
		Desain
		Bisnis
		Bahasa & Sastra

	eksplor pendidikan
		peta view
		card view

	deg-degan matters
		input kelas berapa → di section, saved localStorage
			kelas 10
			kelas 11
			kelas 12
		output setelah input dipilih
			countdown DD · HH · MM · SS
			referensi snpmb.id/jadwal-penting
		cta
			btn eksplorasi bidang ilmu
			btn temukan kampus
\`\`\`

---

## Contoh Salah (JANGAN lakukan ini)

❌ Pakai tree chars:
\`\`\`
├── hero
│   └── btn mulai jelajahi
\`\`\`

❌ Tanpa code block:
hero
    btn mulai jelajahi

❌ Pakai bullet/dash:
- hero
  - btn mulai jelajahi

---

## Kapan pakai skill ini

- User bilang "pakai tabs", "format tabs", "pakai tab"
- User minta flow tree / sitemap / struktur / user flow
- User bilang "tanpa simbol", "tanpa karakter aneh"
- User bilang "tree tapi pakai tab"
- Setiap kali output berupa hierarki konten yang butuh indentasi visual