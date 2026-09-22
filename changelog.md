# Changelog

Semua perubahan penting pada proyek ini didokumentasikan di file ini.

Format berdasarkan [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
dan proyek ini mengikuti [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
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