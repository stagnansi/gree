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
- Code block: `lineNos = false` di hugo.toml (hilangkan nomor baris)
- Code block: `font-family: var(--font-mono)` di `code`
- Code block styling: padding 14px di wrapper, background di wrapper, `border-radius: 0`, `line-height: 0` di `<pre>` (fix strut), `overflow-y: hidden`, `line-height: 1.4` di `pre span`
- Tabel: border-collapse + border 1px `#ddd` + padding `4px 8px` + `font-family: var(--font-mono)`
- Mark (`==teks==`): square (border-radius 0), padding dirapetin (`0`)
- Visited link: warna disamakan dengan link color (`--link-color`)
- URL link: auto-detect + `font-family: var(--font-mono)` (via JS di `custom_body.html`)
- Plain URL di body text: auto-link jadi `<a>` + mono (via JS)
- Code block indented (4 spasi): `overflow-x: auto` di `<pre>` polos
- Override `layouts/_default/single.html`: `<h1>{{ .Title }}</h1>` untuk semua halaman (kecuali Home)
- Override `layouts/_default/list.html`: `<h1>{{ .Title }}</h1>` untuk section list
- UL (kecuali `ul.blog-posts`): `list-style: none` + prefix `→` via `::before`
- `hugo.toml`: `disableKinds` tambah `"term"`

### Removed
- `static/images/favicon.png` (favicon default Bear Blog)
- `static/images/share.png` + folder `static/images/` (portal internal, preview share tidak diperlukan)
- `hugo.toml`: `params.images` (referensi ke `share.png` dihapus)
- `content/blog/markdown-syntax.md`: `tags = [...]` dari frontmatter (tags tidak dipakai)
- Folder kosong: `assets/`, `data/`, `i18n/`
### Removed
- (kosong)

[Unreleased]: https://github.com/stagnansi/gree/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/stagnansi/gree/releases/tag/v0.1.0