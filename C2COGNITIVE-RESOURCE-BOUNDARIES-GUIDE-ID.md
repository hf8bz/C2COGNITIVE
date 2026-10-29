# C2Cognitive | Pembatasan Resource dan Workspace Sementara

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Pengaman di sekitar eksekusi.

**Jalur sebelumnya:** Eksekusi tool dan QA lama berjalan dalam budget yang dinyatakan; clone repositori tanpa batas atau subprocess yatim dapat menghabiskan resource walaupun business logic lolos.

**Pemicu baru:** Scanner, audit, snapshot, regresi, salinan fixture atau command lama membuat file sementara atau child process.

## Alur proses dari awal sampai akhir

1. Tentukan allowlist file yang tepat serta batas estimasi byte/file; jangan menyalin root proyek secara rekursif.
2. Periksa tujuan sementara dan jenis penyimpanan. Jangan diam-diam memilih RAM filesystem seperti `/dev/shm`.
3. Alokasikan hanya workspace milik proses, jalankan dengan timeout, batas memori dan output serta pemilik cleanup.
4. Hentikan lane terkait saat batas byte, file, output, waktu atau proses tercapai; laporkan sisa pekerjaan sebagai NOT-RUN.
5. Saat exit normal atau exception bersihkan hanya resource milik proses; jangan menghapus folder sementara host secara luas.
6. Ulangi tes terbatas dan periksa residu sebelum menyatakan gate resource lokal selesai.

### Keputusan / berhenti / pemulihan

Runner resource-gate Linux/WSL melaporkan unsupported di Windows native, bukan mengklaim PASS tanpa batas.

## Diagram proses

```text
Path target eksplisit + budget
        |
  allowlist sparse / preflight storage
        |
  workspace sementara milik proses
        |
  proses + output + timeout terbatas
        |
  batas terlampaui? -- ya --> suspend / NOT-RUN
        | tidak                       |
  verifikasi hasil nyata          cleanup milik proses
        |                         /
  cleanup + cek residu ----------+
```

## Apakah struktur proses sebelumnya berubah?

Membungkus eksekusi tambahan dan QA. Tidak menulis ulang workflow produk atau mengizinkan pembersihan data bukan miliknya.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: test butuh tiga source file, tetapi script fixture mencoba menyalin seluruh monorepo. Preflight allowlist menolak sebelum disk habis.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/quality/run_resource_gates.py --iterations 200
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `scripts/lib/temp_safety.py`
- `.agent/runbooks/temp-workspace-safety.md`
- `scripts/quality/run_resource_gates.py`
- `scripts/quality/performance_budget.py`
- `docs/RESOURCE-CONTINUITY-HARDENING.md`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
