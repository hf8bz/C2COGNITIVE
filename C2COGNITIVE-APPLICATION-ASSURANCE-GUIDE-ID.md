# C2Cognitive | Profil Kapabilitas dan Gate Penyelesaian Aplikasi

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Perluasan gate penyelesaian bersyarat.

**Jalur sebelumnya:** Penerimaan Goal, rencana exact write, dan bukti pengujian yang sudah terdokumentasi tetap menjadi dasar. Build atau unit test berhasil saja tidak membuktikan semua perilaku aplikasi.

**Pemicu baru:** Aplikasi nyata mempunyai perilaku fungsional, keamanan, integrasi, akuntansi, aksesibilitas, atau operasional yang wajib diterima untuk rilis.

## Alur proses dari awal sampai akhir

1. Bangun profil kapabilitas berdasarkan source dengan nilai `true`, `false` atau `unknown` untuk setiap kapabilitas yang didukung.
2. Validasi profil. Kapabilitas kritis yang belum diketahui, termasuk otorisasi, pembayaran dan isolasi tenant, tidak boleh diam-diam dianggap tidak ada.
3. Bangun ID obligation wajib dari baseline serta kapabilitas yang benar-benar bernilai true; baris awal berstatus blocked menunggu bukti.
4. Ikat setiap obligation pada requirement nyata, build, aktor, environment, hasil yang diharapkan secara independen, dan bukti tepat.
5. Klasifikasikan tiap obligation sebagai verified, not applicable dengan alasan dan otoritas, atau blocked beserta dependensinya.
6. Panggil completion gate secara eksplisit untuk proyek ini. Obligation hilang, tidak valid atau blocked membuat assessment belum siap; gate perubahan dan approval tetap berlaku terpisah.

### Keputusan / berhenti / pemulihan

`scripts/assurance/application.py` menyediakan `validate-profile`, `required`, `generate`, `validate-obligations` dan `gate`. Hasil assurance ready bukan izin deploy.

## Diagram proses

```text
Profil proyek nyata
        |
  validasi true/false/unknown
        |
  ID obligation wajib
        |
  tes nyata + bukti berskop
        |
  panggil completion gate
        |
  valid dan semua wajib selesai?
        | tidak -> BLOCKED / INVALID
        | ya
  readiness saja (bukan izin deploy)
```

## Apakah struktur proses sebelumnya berubah?

Menyediakan keputusan kesiapan setelah verifikasi ketika operator atau host memanggil CLI application assurance. Gate dapat memblokir klaim completion yang relevan, tetapi tidak otomatis mencegat setiap Goal atau mengubah otoritas tulis.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: marketplace menyatakan `payments=true`, `multi_tenant=true`. UI pembelian berhasil tidak dapat menutup obligation idempotensi pembayaran, verifikasi webhook, atau penolakan akses antartenant.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/assurance/application.py required <project-profile.json>
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `scripts/assurance/application.py`
- `scripts/assurance/evidence.py`
- `.agent/runbooks/application-capability-profile.md`
- `.agent/runbooks/comprehensive-qa-audit.md`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
