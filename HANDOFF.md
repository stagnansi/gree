# Handoff — Gree BKS Hugo Project

## Status Proyek
- Repo: github.com/stagnansi/gree
- Live: greebks.pages.dev
- Cloudflare Pages project: greebks (auto-deploy dari main)
- Hugo version: 0.165.0 (env var `HUGO_VERSION` di Cloudflare)
- Timezone: Asia/Jakarta (di hugo.toml + env var `TZ` di Cloudflare)
- Lokal folder: D:\Hugo\Gree
- Alias: `hs` = hugo server -D
- Current version: v0.1.0 (2026-09-23) + Unreleased changes (lihat changelog.md)

## Struktur Kunci
- Theme: hugo-bearblog (submodule)
- Override di root project: `layouts/_default/baseof.html`, `layouts/partials/footer.html`, `layouts/partials/custom_head.html`, `layouts/partials/nav.html`
- File tema TIDAK disentuh, semua override di root project

## Konfigurasi Aktif
- `hugo.toml`: locale=id, timeZone=Asia/Jakarta, mark extension aktif
- `baseof.html`: `.Site.Language.Locale` (bukan deprecated `.Site.LanguageCode`), title dengan conditional `.IsHome`
- Dark mode dimatikan (override `prefers-color-scheme`)
- Markdown `==mark==` → background kuning `#ffff00`

## Color Palette
- Heading: `rgb(30 41 59)` (slate-800)
- Text: `rgb(71 85 105)` (slate-600)
- Link: `rgb(13 82 157)` (biru medium)
- Dark override disamain dengan base (light mode dipaksa)

## Tipografi
- `--font-main`: InterDisplay (heading)
- `--font-secondary`: Inter (body)
- `--font-mono`: IBM Plex Mono
- Slashed zero global: `font-feature-settings: 'zero' 1`
- Font CJK: Noto Sans SC Subset (self-hosted, 8 karakter, 1.8 KB)

## Navbar Responsif
- Grid responsif: 5 → 4 → 3 → 2 kolom (breakpoint 720px / 620px / 340px)
- `grid-template-columns: repeat(N, max-content)` + `justify-content: space-between`
- Gap `0 12px` (row-gap 0, column-gap 12px)
- `white-space: nowrap` untuk cegah wrapping menu 2-kata
- Arrow prefix `→` via `.nav-arrow` di luar `<a>` (tidak bisa diklik, `aria-hidden`, `user-select: none`)
- Override `layouts/partials/nav.html` untuk wrapper `.nav-item`
- `nav a { margin-right: 0 }` — netralkan margin tema (8px) yang konflik dengan grid gap

## Footer Custom (Easter Egg "Nameplate AC")
- Layout: 4 baris (GREE+✱ / BARA + IM0ET·2026 / hanzi / ZHUHAI × BEKAZHI)
- Width: `100%` dengan `max-width: 240px`, `margin: 0 auto` (center)
- Base font: `calc(var(--font-scale) * 0.8)`
- Kipas ✱ berputar 3s/rotation
- `line-height: 1` di span untuk sejajarkan mono vs Inter
- `0` di IM0ET: Inter slashed (bukan mono, karena mono dotted)

## Versioning
- Semantic Versioning (MAJOR.MINOR.PATCH)
- Changelog format: Keep a Changelog
- Rilis ditandai dengan `git tag vX.Y.Z` + push tag
- Current: **v0.1.0** (2026-09-23)

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

## Riwayat Batch

### Batch 1-2 (SELESAI): Setup + Theme
- Hugo + hugo-bearblog setup
- Tipografi overhaul (Inter, InterDisplay, IBM Plex Mono)
- Footer custom "nameplate AC"
- Mark extension, timezone fix, deprecated API fix

### Batch 3 (SELESAI): Menu Cleanup
- 12 halaman baru: Pricelist, Birthday, Compro, Installer, Internal, Kartu Garansi, Katalog, Kode Eror, Sertifikat, Surat, Referral, Always On
- Hapus hugo.md, bear.md (demo tema)
- Home dihapus dari nav (menu = main dihapus dari _index.md)
- Blog weight: 100 → 130
- Konten homepage masih demo (belum diganti)

### Batch 3.5 (SELESAI): Navbar Refinement
- Grid responsif 5-4-3-2 kolom (breakpoint 720/620/340)
- Arrow prefix `→` di luar link
- Override `nav.html`

### Batch 3.8 (SELESAI): Mark + Link + H1
- Mark (`==teks==`): square + padding 0 (rapet)
- Visited link disamakan dengan link color
- URL auto-detect → `font-family: var(--font-mono)`
- Plain URL di body text auto-link jadi `<a>` + mono (JS, skip di `<pre>`/`<code>`)
- Code block indented (4 spasi): scroll horizontal via `pre { overflow-x: auto }`
- Override `single.html` + `list.html`: semua halaman punya `<h1>` (Home skip, pakai h1 manual di konten)
- Catatan: `mark` rapet butuh padding 0 karena line-height body (1.5) bikin ruang vertikal ekstra

### Batch 3.7 (SELESAI): Markdown Styling + Cleanup
- Tabel: border collapse + mono font
- Code block: no line numbers, IBM Plex Mono, padding fix (strut/leading fix via line-height 0 di pre + 1.4 di span), border-radius 0
- UL (kecuali blog-posts): prefix `→` via `::before`
- `hugo.toml`: `disableKinds` tambah `"term"`
- `content/blog/markdown-syntax.md`: hapus tags dari frontmatter
- Cleanup: hapus semua `.bak`, folder kosong (`assets/`, `data/`, `i18n/`), tambah `*.bak` ke `.gitignore`
- Audit CSS: duplikat selector (`:root` 2x, `nav` 4x) semua intentional (dark mode override + responsive breakpoint), tidak ada dead code
- Pelajaran: strut/leading space di code block berasal dari `<pre>` `line-height`, fix dengan `line-height: 0` di pre + `1.4` di `span` (karena Hugo bungkus tiap baris dalam `<span style="display:flex">`)

### Batch 3.6 (SELESAI): Favicon + Homepage + Utilitas
- Favicon Gree Indonesia (dari gree.id) ganti default Bear (commit fb2ce55)
- Homepage custom: hero "Portal Internal" + callout RAHASIA (mark kuning) (commit 03cad85)
- Font hanzi: kembali ke self-host subset (drop Google Fonts Noto)
- `blockquote { font-style: normal }` global
- Emoji user-select:none via JS (custom_body.html baru)
- Back-to-top kondisional di footer (muncul hanya kalau scrollable)
- Hapus share.png + folder images/ (portal internal)
- Audit duplikasi CSS + dead code: CLEAN

### Batch 4 (IN PROGRESS): Konten
- [SELESAI] Favicon resmi Gree Indonesia (commit fb2ce55)
- [SELESAI] Homepage custom (hero + callout RAHASIA) (commit 03cad85)
- [SELESAI] Emoji user-select:none + back-to-top kondisional (commit 03cad85)
- [SELESAI] Hapus share.png + referensi (portal internal, no preview)
- [SELESAI] Pricelist: tabel per wilayah + legend + `<br>` + mark FLFE
- [SELESAI] Birthday: tabel ultah + CA reminder + link Sheets
- [SELESAI] Compro: 2 brand (FLiFE/Gree) + link pptx + `.mono` tanggal
- [SELESAI] Render hook external link + goldmark unsafe=true
- [SELESAI] Utility class `.mono` + inline code alignment fix
- [TODO] 9 halaman lain (Installer, Internal, Kartu Garansi, Katalog, Kode Eror, Sertifikat, Surat, Referral, Always On)
- [TODO] Blog post pertama (markdown-syntax.md masih demo Bear, biarkan untuk cek markdown)

### Batch 5 (KANDIDAT): Sidebar
- Ganti navbar horizontal jadi sidebar kiri (opsi F dari preview)
- Butuh modifikasi baseof.html + header.html + CSS

## Catatan Teknis
- PowerShell 7.6.6 (bukan 5.1)
- Windows Terminal dengan split pane (pane 1: hs, pane 2: cmd)
- Hugo server auto-reload, tapi kalau port 1313 dipakai, otomatis pindah ke 2820
- Gunakan absolute path untuk .NET methods (`[System.IO.File]::ReadAllText`)
- Here-string multi-line rawan error di PS — pakai array join `@() -join` untuk yang kompleks
- Single-quoted here-string `@'...'@` aman untuk konten dengan backtick/quote
- `git --no-pager` untuk hindari terjebak di pager `less`