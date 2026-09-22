# Paradoxical Man — funnel

Landing page + funnel jualan produk **Paradoxical Man**. Ini halaman publik yang
dipakai buat konversi, jadi copy-nya sensitif — jangan diubah tanpa diminta.

> Untuk pekerjaan user-facing yang menyentuh brand, baca `../BRAND.md` dulu.
> Aturan universal berlaku dari `../AGENTS.md`.

## Fakta repo
- Folder lokal `paradoxical-man-lp/`, repo `nychothesis/paradoxical-man` (publik).
- Live: **https://nychothesis.com/paradoxical-man/**
- Deploy: push ke `main`, Pages auto-update. Ga ada build step.

## Halaman
| File | Fungsi |
|---|---|
| `index.html` | Landing utama (~83 KB). Normal = full price. `?oto=1` = harga diskon + timer + **2 tombol pilihan** ("bundling + e-course" checkout, atau "ikut webinar aja" → `webinar-thanks.html`) |
| `optin.html` | Form ambil PDF gratis, dari link organik (homepage `nychothesis.com` + footer, masih aktif dipake, jangan dianggep dead code) → langsung `index.html?oto=1` |
| `dm.html` | Form ambil PDF gratis juga, tapi khusus link dari DM automation → `thanks.html` (bukan langsung OTO) |
| `thanks.html` | "PDF otw, cek email" abis `dm.html`. Promosi webinar itu CTA utama di sini (paling atas), bukan cuma tempelan |
| `webinar.html` | Form daftar webinar gratis (data doang) → langsung `index.html?oto=1` |
| `webinar-thanks.html` | "Lu udah terdaftar" + link join WA grup peserta webinar. Dituju dari tombol "ikut webinar aja" di `index.html?oto=1`, ga ada penawaran course lagi di sini (itu keputusannya udah kejadian sebelum sampe sini) |
| `funnel.css` | Style bersama semua halaman kecuali `index.html` (dia punya `<style>` sendiri, ga nge-link `funnel.css`) |

`ringkas.html` udah ga ada. Dia dipromosiin jadi `index.html`, dan yang lama
dibuang (masih bisa diambil dari riwayat git). `pilihan.html` juga sempet ada
sebentar (22 Sep 2026, halaman minimalis 2-tombol terpisah) tapi itu salah
paham arahan mentor Mike, langsung dicabut hari yang sama. Kalo nemu sisa
referensi ke `pilihan.html` di tempat lain (vault, Discord), itu basi.

Alur lengkap (per 2026-09-22, dikonfirmasi mentor Mike): `webinar.html` →
`index.html?oto=1` → 2 tombol di situ langsung: `webinar-thanks.html` (WA
grup) *atau* checkout. `dm.html`/`optin.html` → `thanks.html` → CTA balik ke
`webinar.html`. Detail lengkap ada di vault
`2 - Projects/Nychothesis/📀 Paradoxical Man.md`.

## Kode voucher
| Kode | Muncul di | Potongan |
|---|---|---|
| `OTO70` | cuma di mode `?oto=1` | Rp70.000 |
| `FPDF50` | ga di sini, adanya di PDF gratis | Rp50.000 |

Halaman normal sengaja **ga nampilin kode apapun**, harganya penuh Rp299.000.

**`index.html` punya dua mode**: normal dan `?oto=1` (one-time offer) — copy-nya
beda. Kalau ngedit atau proofread, **cek dua-duanya**, gampang kelewat.

## REVISI.md — alur kerja revisi
`REVISI.md` itu file **lokal, di-gitignore, ga ke-push**. Alurnya: Nicho naro
draft/antrian revisi di situ, lalu bilang **"apply REVISI.md"** — baru dikerjakan.
Jangan otomatis apply isinya tanpa diminta.

## Yang di-gitignore
`REVISI.md`, `.DS_Store`, `assets/SCR-*.jpg`, `assets/*-Photoroom.png` — screenshot
mentah & aset kerja, sengaja ga ikut ke repo publik.

## Catatan kerja
- Sudah dirapikan buat HP: baris from–to ditumpuk (bukan dua kolom sempit).
- Ada penanda "Analoginya" di bagian analogi kupu-kupu.
- `.panel` di `funnel.css` ga punya margin sendiri. Dua `.panel` yang ditumpuk
  langsung (tanpa elemen lain di antaranya) bikin sudut bulatnya nabrak dan
  keliatan ada celah aneh. Kasih `margin-bottom` manual di panel sebelumnya
  kalau nyusun beberapa `.panel` berurutan (lihat `webinar.html`).
- **Jangan nempelin elemen baru (voucher box, tombol, dll) ke dalem
  `.product-poster`/`.webinar-poster`.** Kartu itu punya tinggi TETAP
  (`aspect-ratio`) + `overflow:hidden` buat jaga sudut gambar. Kalo ada child-nya
  yang juga pake `overflow:hidden` (misal `.voucher`), flexbox/grid nurunin
  "automatic minimum size"-nya jadi 0, jadi kalo ruang kurang, browser DIEM-DIEM
  meres kontennya sampe kepotong, bukan overflow atau error di console. Ga
  ketauan dari nge-grep kode, cuma ketauan kalo beneran diukur (`clientHeight`
  vs `scrollHeight`) atau discreenshot penuh. Taro elemen tambahan itu SETELAH
  section poster-nya kelar (`.insertAdjacentElement('afterend', ...)`), bukan di
  dalemnya.
- **Jangan pake `-->` sebagai panah ASCII di dalem komentar HTML `<!-- -->`.**
  Itu nutup komentarnya beneran di situ (HTML tokenizer nyari literal `-->`,
  bukan cuma `--`), sisa isi komentar (bisa belasan baris) jadi teks visible di
  halaman. Kejadian di `thanks.html`, bocor ke production tanpa ada error/warning
  apapun. Pake `->` (satu strip) atau kata biasa buat gambarin arah alur.
- **Ngecek "halaman ini masih dipake apa nggak" jangan cuma grep repo lokal.**
  `optin.html` sempet disangka dead code karena ga ada `href` ke situ di HTML
  manapun dalam repo ini, padahal dia aktif dilink dari homepage
  `nychothesis.com` (kartu PDF + footer), yang itu sendiri dituju dari bio IG.
  Buat mastiin, cek live site/homepage-nya juga, jangan cuma grep `*.html` di
  folder ini.
