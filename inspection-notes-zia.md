# 📋 Inspeksi Cerita Zia (Shinoa Hoshiyume)

> **Tanggal:** 8 Juli 2026
> **Diinspeksi oleh:** Jarvis (atas instruksi Kak Sari)
> **Tujuan:** Catatan untuk Zia (Shinoa) — biar tau apa aja yang udah diperbaiki dan kenapa

---

## Daftar Cerita

| Cerita | Status | Folder |
|---|---|---|
| ✅ **Only One** | Selesai, tinggal polishing kecil | `sari/only-one` |
| ✅ **Death or Separation** | Selesai, udah di-compile ulang | `sari/death-or-separation` |
| ✅ **Why?** | Selesai (ada catatan khusus) | `sari/why` |

---

## 1. Only One

### Lokasi
- **Source of truth (Gitea):** `sari/only-one/` di repo `sari/cerivitas-cyoastories`
- **Zia punya repo sendiri:** `Zia.Fithraturrahmah/cerivitas-cyoastories` (folder `shinoa-only-one/`)
- **Live di GitHub Pages:** https://sarinursita.github.io/cerivitas-cyoastories/only-one/

### Yang udah diperbaiki

#### ✅ Index.md — Metadata digabung
Sebelumnya info terpisah di dua tempat:
- **sari/only-one/index.md** → penulis bener (`Shinoa Hoshiyume`) tapi premis kosong
- **Zia.Fithraturrahmah/shinoa-only-one/index.md** → premis udah diisi (`Pagi-pagi di sekolah...`) tapi penulis masih `[nama]`

**Sekarang `sari/only-one/index.md` paling lengkap:**
```markdown
# Only One

- **Penulis:** Shinoa Hoshiyume
- **Genre:** Romance
- **Tags:** drama, persahabatan, sekolah
- **Rating:** PG
- **Date:** 2026-06-28
- **Jumlah scene:** 14

**Premis:** Pagi-pagi di sekolah, Aysel harus memilih antara nyapa Hali atau Kaizo duluan. Pilihan kecil yang membawa konsekuensi tak terduga di sisa harinya.
```

#### ✅ Konten scene IDENTIK
Semua scene (01-14) di `sari/only-one` vs `Zia.Fithraturrahmah/shinoa-only-one` **sama persis** — beda 0 baris. ✅

### Catatan
- Cerita ini genre **Romance** — tema sekolah, pilihan Aysel antara Hali dan Kaizo
- Bisa di-compile ulang kalo perlu pake `gen-cyoa-html.py`

---

## 2. Death or Separation

### Lokasi
- **Source of truth:** `sari/death-or-separation/`
- **Live di GitHub Pages:** https://sarinursita.github.io/cerivitas-cyoastories/death-or-separation/
- **Draft docx:** `/home/saristudio/cyoa-books/death-or-separation.docx`

### Yang udah diperbaiki

#### ✅ Konten .md files vs compiled index.html — SAMA
Semua 11 scene (01-07b) udah dicek — narrative, choices, branching, ending text **identik**. ✅

#### ✅ Hapus marker `<!-- Status: belum-selesai -->` dari scene-01 sampai scene-05b
Marker ini bikin scene keliatan "belum selesai" padahal ceritanya udah lengkap. Udah dihapus dari 8 file.

#### ✅ Hapus `<!-- Status: END -->` dari scene-06, 07a, 07b
HTML comment `<!-- Status: END -->` bakal kelihatan sebagai teks mentah di player.html (karena di-escape). Udah diganti pake `**Status:** END` yang proper.

#### ✅ Fix compiler `gen-cyoa-html.py` — 2 bug:
1. **Urutan `esc()`** → Tadinya `**bold**` diubah ke `<strong>` DULU baru di-`esc()`. Urutan bener: `esc()` dulu, baru markdown→HTML.
2. **Escaping `\n`** → Di Python f-string, `\n` di-interpret sebagai newline, bukan literal `\n`. Sekarang pake `\\n` yang bener.

#### ✅ Isi premis di index.md
Dari `(nanti diisi)` jadi deskripsi cerita yang proper.

### Tree cerita
```
Scene 1 — Medan perang, saudara Ice semua Reverse
  ├─ Scene 2A: Ice maju duluan → Scene 3A/3B → Scene 4 → Scene 5A/5B
  └─ Scene 2B: Noa ajak Ice strategi → Scene 3A/3B → Scene 4 → Scene 5A/5B
Scene 4 — GEMPA tangkap Noa!
  ├─ Scene 5A: Ice lawan Gempa → Scene 6
  └─ Scene 5B: Ice coba nego → Scene 6
Scene 6 — Noa jatuh di pelukan Ice 💔
  ├─ Scene 7A: Ending — Ice mati bersama Noa 🏁
  └─ Scene 7B: Ending — Ice menjadi Reverse 🏁
```

### Catatan
- Genre **Fantasy, Angst** — Boboiboy fanfiction
- Ending marker udah proper (`**Status:** END`)
- Udah di-recompile pake compiler yang udah dibenerin

---

## 3. Why?

### Lokasi
- **Source of truth:** `sari/why/`
- **Live di GitHub Pages:** https://sarinursita.github.io/cerivitas-cyoastories/why/
- **Draft docx:** `/home/saristudio/cyoa-books/why.docx`

### ⚠️ PENTING — Cerita ini PUNYA CUSTOM HTML!

Why? **bukan** pake compiler standar `gen-cyoa-html.py`. Dia punya HTML custom yang dibuat khusus dengan fitur:

| Fitur | Ada di HTML custom? | Standar compiler? |
|---|---|---|
| 🖼️ SVG images inline (istana, dapur, halaman, dll) | ✅ 6 scene | ❌ |
| 🏠 Title screen custom (premis, author, genre) | ✅ | ❌ |
| 💬 Talk counter (hitung siapa yg diajak ngobrol) | ✅ (sekarang cuma info) | ❌ |
| 🔀 Dynamic branching scene7 (dulu) | ❌ (udah dihapus) | ❌ |

### Yang udah diperbaiki

#### ✅ File rename — match format player.html (4 file)
| Sebelum | Sesudah |
|---|---|
| `scene-2b.md` | `scene-02b.md` |
| `scene-3b.md` | `scene-03b.md` |
| `scene-4b.md` | `scene-04b.md` |
| `scene-5b.md` | `scene-05b.md` |

#### ✅ Scene-06 — 3 pilihan non-spoiler
**Dulu:** Cuma 1 pilihan `[Scene 7]` → talk counter tentuin ending (7a/7b/7c)
**Sekarang:** 3 pilihan langsung:

```markdown
- [Scene 7A]: "Aku tahu siapa yang bisa dipercaya..."
- [Scene 7B]: "Semoga ini cukup..."
- [Scene 7C]: "Aku tidak tahu harus percaya siapa."
```

#### ✅ Ending marker — ganti `<!-- Status: END -->` jadi `**Status:** END`
HTML comment `<!-- Status: END -->` di scene-7a, 7b, 7c bakal kelihatan di player.html. Udah diganti.

#### ✅ Fix `**bold**` rendering di HTML custom
Renderer naratif tadinya cuma `esc(p)` doang — sekarang pake:
```javascript
esc(p).replace(/\*\*(.+?)\*\*/g, "<strong>$1</strong>")
      .replace(/\*(.+?)\*/g, "<em>$1</em>")
```

#### ✅ Talk counter branching — tetap aktif di HTML
HTML custom pake talk counter buat tentuin ending (seperti desain aslinya). Scene-6 cuma punya 1 pilihan `"Lanjutkan..."` yang mengarah ke `scene7`, lalu:

```javascript
if (sceneId === "scene7") {
    sceneId = talkCount >= 4 ? "scene7a" : talkCount >= 3 ? "scene7b" : "scene7c";
}
```

Sementara .md files punya 3 pilihan eksplisit buat kompatibilitas player.html & cetak buku.

### Tree cerita
```
Scene 1 — Bangun di Istana 🏰
  └── Scene 2: Koki di Dapur
       ├── Scene 2B: Cerita Koki (talk +1) → Scene 3
       └── Scene 3: Ksatria di Halaman
            ├── Scene 3B: Cerita Ksatria (talk +1) → Scene 4
            └── Scene 4: Penasihat di Perpustakaan
                 ├── Scene 4B: Cerita Penasihat (talk +1) → Scene 5
                 └── Scene 5: Pelayan di Lorong
                      ├── Scene 5B: Cerita Pelayan (talk +1) → Scene 6
                      └── Scene 6: Malam Yang Menentukan
                           ├── Scene 7A: Good Ending 🏆
                           ├── Scene 7B: Bittersweet ⚠️
                           └── Scene 7C: True Ending 💀 (Plot Twist!)
```

### Catatan Penting untuk ke Depan
1. **Jangan di-recompile pake `gen-cyoa-html.py`!** Nanti SVG images & title screen ilang
2. **Kalo mau cetak buku:** Scene-06 pilihan 3 (7A/7B/7C) udah siap untuk format buku
3. **Kalo mau balancing ending:** Sekarang pemain langsung milih ending di scene-6 (nggak otomatis dari talk counter)
4. **Talk counter** dipertahankan di HTML sebagai info, bukan penentu ending lagi
5. **Plot twist di index.md:** "Di ending terburuk, pembaca lupa kalau dirinya bukanlah sang putri."
6. **Note:** SVG images dibuat inline di HTML — kalo mau dipake ulang, perlu di-export dari HTML

---

## Format Standar .md Files (untuk player.html)

Biar kompatibel sama `player.html`, format yang diharapkan:

```markdown
# Scene X: Judul Scene

**Setting:** Tempat — waktu, suasana
**Karakter:** Karakter1, Karakter2

Narrative text...
Bisa pake **bold** dan *italic*.

---

**Pilihan:**
- [Scene XA]: Teks pilihan
- [Scene XB]: Teks pilihan lainnya

**Status:** END    ← untuk ending scene
```

### Aturan:
- **Title:** `# Scene X: ...` (angka bisa 1, 2A, 7C, dll)
- **Metadata:** `**Setting:**`, `**Karakter:**`
- **Separator:** `---` antara narasi dan pilihan
- **Choices:** `- [Scene XA]: Teks` (pakai `[Scene ...]`, capital S)
- **File naming:** `scene-01.md`, `scene-02b.md` (pakai leading zero untuk digit pertama)
- **Ending marker:** `**Status:** END` (bukan HTML comment)
- **Markdown:** `**bold**` dan `*italic*` akan di-render otomatis
