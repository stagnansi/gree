# Handoff — Gree BKS Hugo Project

## Status Proyek
- Repo: github.com/stagnansi/gree
- Live: greebks.pages.dev
- Cloudflare Pages project: greebks (auto-deploy dari main)
- Hugo version: 0.165.0 (env var `HUGO_VERSION` di Cloudflare)
- Timezone: Asia/Jakarta (di hugo.toml + env var `TZ` di Cloudflare)
- Lokal folder: D:\Hugo\Gree
- Alias: `hs` = hugo server -D

## Struktur Kunci
- Theme: hugo-bearblog (submodule)
- Override di root project: `layouts/_default/baseof.html`, `layouts/partials/footer.html`, `layouts/partials/custom_head.html`
- File tema TIDAK disentuh, semua override di root project

## Konfigurasi Aktif
- `hugo.toml`: locale=id, timeZone=Asia/Jakarta, mark extension aktif
- `baseof.html`: `.Site.Language.Locale` (bukan deprecated `.Site.LanguageCode`), title dengan conditional `.IsHome`
- Dark mode dimatikan (override `prefers-color-scheme`)
- Markdown `==mark==` → background kuning `#ffff00`

## Tipografi
- `--font-main`: InterDisplay (heading)
- `--font-secondary`: Inter (body)
- `--font-mono`: IBM Plex Mono
- Slashed zero global: `font-feature-settings: 'zero' 1`
- Font CJK: Noto Sans SC Subset (self-hosted, 8 karakter, 1.8 KB)

## Footer Custom (Easter Egg "Nameplate AC")
- Layout: 4 baris (GREE+✱ / BARA + IM0ET·2026 / hanzi / ZHUHAI × BEKAZHI)
- Width: `100%` dengan `max-width: 240px`, `margin: 0 auto` (center)
- Base font: `calc(var(--font-scale) * 0.8)`
- Kipas ✱ berputar 3s/rotation
- `line-height: 1` di span untuk sejajarkan mono vs Inter
- `0` di IM0ET: Inter slashed (bukan mono, karena mono dotted)

## Aturan Kerja (Ritme)
1. Kasih cmd → user paste hasil → verifikasi error
2. Cek keterkaitan file lain
3. Cek localhost (Comet browser)
4. Catat di changelog.md (Keep a Changelog format)
5. Skip README sampai web siap launch
6. Commit + push
7. Cek ulang tidak ada yang ketinggalan

## Aturan Kustomisasi
- Jangan sok ngide / improve di luar permintaan
- Jangan sentuh file di themes/, semua override di root project
- Cek dulu CSS asli tema, jangan duplikat
- Konfirmasi sebelum override properti yang sudah ada
- Referensi selalu ke standar baku (Keep a Changelog, Semantic Versioning, dll)

## Batch 3 (SELESAI): Menu Cleanup
- 12 halaman baru: Pricelist, Birthday, Compro, Installer, Internal, Kartu Garansi, Katalog, Kode Eror, Sertifikat, Surat, Referral, Always On
- Hapus hugo.md, bear.md (demo tema)
- Home dihapus dari nav (menu = main dihapus dari _index.md)
- Navbar: grid 4 kolom, font normal
- Blog weight: 100 -> 130
- Konten homepage masih demo (belum diganti)

## Batch 4 (KANDIDAT): Konten
- Isi konten 12 halaman (Pricelist, dll)
- Ganti konten homepage dari demo tema
- Blog post pertama
- Ganti favicon & share.png

## Batch 5 (KANDIDAT): Sidebar
- Ganti navbar horizontal jadi sidebar kiri (opsi F dari preview)
- Butuh modifikasi baseof.html + header.html + CSS
## Pending / Kandidat Batch 3
- Menu cleanup (hapus/ubah menu Hugo, Bear, Blog)
- Konten homepage (ganti dari demo tema)
- Halaman baru (About, Contact, dll)
- Blog post pertama
- Ganti favicon & share.png (masih default tema)
- Test mark di production

## Catatan Teknis
- PowerShell 7.6.6 (bukan 5.1)
- Windows Terminal dengan split pane (pane 1: hs, pane 2: cmd)
- Hugo server auto-reload, tapi kalau port 1313 dipakai, otomatis pindah ke 2820
- Gunakan absolute path untuk .NET methods (`[System.IO.File]::ReadAllText`)
- Here-string multi-line rawan error di PS — pakai array join `@() -join` untuk yang kompleks