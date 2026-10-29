# C2Cognitive | Migrasi Versi Terjaga dan Continuity Workflow

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Jalur upgrade distribusi terpisah.

**Jalur sebelumnya:** Upgrade repositori yang diotorisasi manusia harus menjaga aplikasi dan Goal yang sudah diadopsi. Mengganti file kontrol saja tidak cukup untuk menjaga aturan kustom.

**Pemicu baru:** Operator memilih memindahkan instalasi dari versi publik sebelumnya yang tepat menuju baseline source lokal yang dibekukan.

## Alur proses dari awal sampai akhir

1. Tentukan bahasa, identitas baseline publik, inventaris path distribusi tepat, dan file governance yang dikustomisasi.
2. Jalankan pemeriksaan read-only sesuai patch terlebih dahulu. Tolak path/digest drift atau baseline tidak dikenal alih-alih mengira hasil merge.
3. Pisahkan file produk, perubahan kustom yang diadopsi, dan generated state dari path template terkelola.
4. Dapatkan persetujuan yang diperlukan untuk modifikasi tepat dan siapkan rollback bernama; jangan mengubah Goal aktif atau completion state secara oportunistis.
5. Terapkan hanya patch yang dinyatakan menggunakan applier terdokumentasi di copy disposable dahulu, lalu periksa inventaris target dan kompatibilitas resume.
6. Untuk file kustom yang berubah, lakukan review tiga arah secara sengaja, bukan menimpa aturan pengguna diam-diam.

### Keputusan / berhenti / pemulihan

Replay patch lokal bukan bukti universal bahwa checkout live cocok dengan predecessor resmi yang diharapkan. Fail closed bila aset tidak identik.

## Diagram proses

```text
Inventaris source publik sebelumnya yang tepat
        |
  preflight digest/path read-only
        |
  berbeda? -- ya --> STOP / rekonsiliasi manual
        | tidak
  rollback bernama + modifikasi tepat berizin
        |
  replay patch disposable + verifikasi target
        |
  path kustom konflik? -- ya --> merge manual tiga arah
        | tidak
  upgrade berskop / validasi ulang Goal dan resume
```

## Apakah struktur proses sebelumnya berubah?

Mengubah distribusi terpasang hanya ketika dimulai secara eksplisit. Bukan Goal baru, migrasi otomatis, atau mutasi GitHub live.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: tim mengubah `.agent/config.yml`. Patch publik yang ketat menolak atau memisahkan konflik; operator harus merekonsiliasi config itu, bukan memaksa overwrite.

## Referensi implementasi di distribusi

- `INSTALL-WORKFLOW-ONLY.prompt.md`
- `START-HERE.md`
- `AGENTS.md`
- `.agent/distribution-files.txt`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
