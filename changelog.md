# Changelog

Semua perubahan penting pada proyek ini didokumentasikan di file ini.

Format berdasarkan [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
dan proyek ini mengikuti [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Homepage custom: hero "Portal Internal" + callout confidential (mark kuning "RAHASIA")
- `layouts/partials/custom_body.html` (baru): JS untuk emoji user-select + back-to-top
- Tombol "↑ KEMBALI KE ATAS" di footer (kondisional via JS, hanya muncul kalau halaman scrollable)

### Changed
- Font hanzi: Google Fonts Noto Sans SC → self-host subset (`static/fonts/noto-sans-sc-subset.woff2`, 1.8 KB)
- `@font-face` 'Noto Sans SC Subset' di-restore di `custom_head.html`
- `blockquote { font-style: normal }` global (override italic default)
- `.emoji` class: `user-select: none` untuk semua emoji (di-wrap via JS)
- Favicon: dari default Bear Blog → favicon resmi Gree Indonesia (`https://gree.id/favicon.ico`)
- `hugo.toml`: `params.favicon` = `"favicon.ico"`
- `static/favicon.ico`: diganti dengan favicon Gree (single-size ICO, 61×60)

### Removed
- `static/images/favicon.png` (favicon default Bear Blog)
## [0.1.0] - 2026-09-23

### Added
- 12 halaman menu baru: Pricelist, Birthday, Compro, Installer, Internal, Kartu Garansi, Katalog, Kode Eror, Sertifikat, Surat, Referral, Always On
- Navbar CSS: grid responsif (5 → 4 → 3 → 2 kolom)
- Navbar arrow prefix `→` di kiri tiap item (via `.nav-arrow`, di luar `<a>`, `aria-hidden`, `user-select: none`)
- Override `layouts/partials/nav.html`: struktur `.nav-item` wrapper untuk arrow di luar link
- Override `layouts/_default/baseof.html`: fix deprecated `.Site.LanguageCode` + title `IsHome`
- Markdown mark extension (==teks==) dengan styling kuning stabilo
- Timezone Asia/Jakarta di hugo.toml untuk fix "future post" issue
- Dark mode dimatikan total via override prefers-color-scheme
- Footer custom bertema "nameplate outdoor unit AC" sebagai easter egg
- Animasi kipas berputar (karakter `&#10033;`, 3 detik per rotasi)
- Font subset Noto Sans SC (self-hosted, 8 karakter) untuk slogan Chinese
- Font Inter & InterDisplay (via rsms.me) untuk heading dan body
- Font IBM Plex Mono (via Google Fonts) sebagai `--font-mono`
- `changelog.md` dengan format Keep a Changelog

### Changed
- Navbar: dari inline default Bear → grid `max-content` + `justify-content: space-between`
- Navbar gap: `0 12px` (row-gap 0, column-gap 12px)
- Navbar `white-space: nowrap` untuk cegah wrapping menu 2-kata
- Navbar `nav a { margin-right: 0 }` — netralkan margin tema yang konflik dengan grid
- Hapus halaman demo `hugo.md` dan `bear.md`
- Hapus `menu = "main"` dari `_index.md` (Home tidak lagi di nav)
- Blog weight diubah dari 100 ke 130
- Title header (`.title h2`) → font-weight 900
- `hugo.toml`: `copyright` → "Copyright © 2026, Bara Imoet."
- `hugo.toml`: `params.description` → "Gree BKS."
- `hugo.toml`: `params.title` → "Gree® BKS"
- `hugo.toml`: `hideMadeWithLine` diaktifkan (footer tema digantikan footer custom)
- Tipografi: heading → InterDisplay, body → Inter, mono → IBM Plex Mono
- Slashed zero aktif secara global via `font-feature-settings: 'zero' 1`
- `time` element → IBM Plex Mono
- Footer plate: fluid width (`max-width: 240px`), ter-center (`margin: 0 auto`), base font `calc(var(--font-scale) * 0.8)`
- `GREE®` di footer → weight 900 italic
- `ZHUHAI × BEKAZHI` dan `2026` di footer → IBM Plex Mono
- Footer `0` di `IM0ET` → Inter slashed (bukan mono, karena mono dotted)

### Fixed
- (kosong)

### Removed
- (kosong)

[Unreleased]: https://github.com/stagnansi/gree/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/stagnansi/gree/releases/tag/v0.1.0