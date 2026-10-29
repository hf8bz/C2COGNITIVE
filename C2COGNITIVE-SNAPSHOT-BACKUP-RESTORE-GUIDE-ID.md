# C2Cognitive | Snapshot, Verifikasi dan Restore Berbasis Allowlist

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Pengaman siklus artefak.

**Jalur sebelumnya:** Rollback bernama tetap wajib untuk edit repositori. Namun copy atau ZIP biasa tidak cukup sebagai bukti bahwa restore aman atau byte-identik.

**Pemicu baru:** Snapshot distribusi lokal, replay backup atau latihan restore terbatas diminta.

## Alur proses dari awal sampai akhir

1. Pilih file source dari `.agent/distribution-files.txt` dan tolak path berbahaya/duplikat/VCS-private atau input symlink/non-regular.
2. Baca metadata source terbatas dan kemas isi file tepat, SHA-256 dan mode file normal yang diperbolehkan.
3. Verifikasi namespace arsip, ukuran anggota, manifest, digest dan mode sebelum restore.
4. Restore ke tujuan *baru* yang belum ada melalui staging, dengan hash check dan sinkronisasi file/direktori.
5. Publikasikan tanpa overwrite tujuan. Jika durabilitas direktori akhir tak bisa dipastikan, tandai INDETERMINATE dan periksa sebelum retry.
6. Bandingkan seluruh byte source terpilih dengan hasil restore. Pertahankan otoritas rollback khusus transaksi untuk perubahan produk.

### Keputusan / berhenti / pemulihan

`pack`, `verify`, dan `restore` adalah operasi berbeda. Restore arsip tidak memberi izin edit repositori live; overwrite tujuan yang ada sengaja ditolak.

## Diagram proses

```text
Allowlist distribusi
        |
  pack file regular + hash + mode
        |
  verifikasi path/ukuran/digest/mode
        |
  valid? -- tidak --> FAIL / tolak
        | ya
  staging hanya ke tujuan baru
        |
  fsync + publikasi tanpa overwrite
        |
  durable? -- tak pasti --> INDETERMINATE / periksa
        | ya
  bandingkan byte source dan hasil restore
```

## Apakah struktur proses sebelumnya berubah?

Menambah mekanisme package/restore lokal yang lebih aman di samping rollback perubahan lama; bukan pengganti backup DB atau disaster recovery produksi.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: ZIP lolos CRC tetapi gagal SHA-256 anggota atau mempunyai path symlink. Restore berhenti sebelum publikasi tujuan.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/quality/repository_snapshot.py verify --archive <snapshot.zip>
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `scripts/quality/repository_snapshot.py`
- `scripts/quality/run_resource_gates.py`
- `.agent/distribution-files.txt`
- `.agent/runbooks/backup-restore.md`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
