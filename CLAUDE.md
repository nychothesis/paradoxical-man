# Paradoxical Man — funnel

Landing page + funnel jualan produk **Paradoxical Man**. Ini halaman publik yang
dipakai buat konversi, jadi copy-nya sensitif — jangan diubah tanpa diminta.

> Profil brand, gaya bahasa, dan preferensi visual ada di `CLAUDE.md` root
> (`Vibe Code/CLAUDE.md`) — berlaku juga di sini, ga perlu diulang.

## Fakta repo
- Folder lokal `paradoxical-man-landing/`, repo `nychothesis/paradoxical-man` (publik).
- Live: **https://nychothesis.com/paradoxical-man/**
- Deploy: push ke `main`, Pages auto-update. Ga ada build step.

## Halaman
| File | Fungsi |
|---|---|
| `index.html` | Landing utama (paling panjang, ~55 KB) |
| `ringkas.html` | Versi ringkas dari landing |
| `optin.html` | Form ambil PDF gratis |
| `thanks.html` | Halaman "cek email lu" setelah opt-in |
| `funnel.css` | Style bersama halaman opt-in & thanks |

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
