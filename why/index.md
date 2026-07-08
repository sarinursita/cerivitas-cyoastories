# Why?

- **Penulis:** Shinoa Hoshiyume
- **Genre:** Fantasy, Misteri
- **Tags:** psychological, mystery, royal, betrayal, multiple-endings
- **Rating:** PG
- **Theme:** dark
- **Date:** 2026-06-29
- **Premis:** Kamu terbangun dalam tubuh seorang putri kerajaan Lumindor yang sedang sakit parah. Semua orang di sekitarmu terlihat kasihan tapi takut bicara jujur. Ternyata, kakakmu sendiri — sang Ratu — adalah dalang di balik semua ini. Bisakah kamu menemukan kebenaran sebelum terlambat?
- **Jumlah scene:** 13 (scene-01 sampai scene-7c)
- **Plot twist:** Di ending terburuk, pembaca lupa kalau dirinya bukanlah sang putri.

---

> **⚠️ Catatan Developer — Why?**
>
> Cerita ini punya **compiled HTML custom** yang berbeda dari cerita lain:
> - Ada **SVG images inline** di setiap scene (istana, dapur, halaman, perpustakaan, lorong, kamar)
> - Ada **title screen custom** (premis, author, genre)
> - Ada **talk counter** (hitung interaksi dengan 4 karakter) — sekarang hanya dipake sebagai info display di scene-6
>
> **Awalnya** scene-06 cuma punya 1 pilihan (`[Scene 7]`), dan ending ditentukan talk counter:
> - talkCount ≥ 4 → scene-7a (Good Ending 🏆)
> - talkCount ≥ 3 → scene-7b (Bittersweet ⚠️)
> - talkCount ≤ 2 → scene-7c (True Ending 💀)
>
> **Sekarang** scene-06 punya 3 pilihan eksplisit ke scene-7a/b/c untuk kompatibilitas:
> - player.html & cetak buku ✅
> - Talk counter dipertahankan di HTML sebagai info aja
>
> **Jika direcompile dengan `gen-cyoa-html.py`:**
> - SVG images ilang ❌
> - Title screen ilang ❌
> - Talk counter ilang ❌
> - Tapi markdown (`**bold**`, `*italic*`) akan ke-render ✅
> - Scene-06 3 pilihan tetap jalan ✅
>
> **Scene files:**
> - Track A (jalan terus): scene-01 → scene-02 → scene-03 → scene-04 → scene-05 → scene-06
> - Track B (ngobrol): scene-0{2,3,4,5}b (masing-masing auto-lanjut ke scene berikutnya)
> - Ending: scene-7a / scene-7b / scene-7c
>
