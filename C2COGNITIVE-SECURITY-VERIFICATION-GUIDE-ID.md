# C2Cognitive | Pengujian Keamanan Terbatas dan Rantai Kegagalan

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Perluasan gate QA berskop.

**Jalur sebelumnya:** Requirement keamanan dan persetujuan operator sudah mengatur pengujian sensitif. Satu retest tidak boleh menghapus kegagalan sebelumnya tanpa hasil yang terhubung.

**Pemicu baru:** Jalur keamanan yang sudah diotorisasi memilih SAST, DAST, fuzz, red-team, atau dependency check untuk subjek dan lingkungan tertentu.

## Alur proses dari awal sampai akhir

1. Tetapkan target, akun, kelas uji, batas efek dan referensi otorisasi; jangan mewarisi izin proyek lain.
2. Buat rencana pengujian yang terikat pada run ID, scope ID dan SHA-256 source.
3. Jalankan hanya tools dan skenario yang diizinkan. Tool, perangkat atau kredensial yang tidak tersedia berarti NOT-RUN.
4. Catat PASS, FAIL, NOT-RUN, NOT-VERIFIED atau N/A per tes terencana dengan referensi bukti tersanitasi dan terbatas.
5. Retest melalui baris baru dengan `retest_of`. Bawa `defect_id` yang sama melalui turunan belum selesai; N/A atau NOT-RUN tidak bisa menghapus kegagalan terbuka.
6. Validasi ledger dan hubungkan temuan belum selesai ke obligation assurance; hanya retest PASS yang cocok yang dapat menutup lineage.

### Keputusan / berhenti / pemulihan

Validator memeriksa pencatatan hasil terstruktur; tidak menjalankan SAST/DAST/pentest sendiri atau membuktikan izin. `--require-complete` mewajibkan seluruh pengujian terencana tercatat.

## Diagram proses

```text
Rencana test sah + hash source
        |
  jalankan SAST/DAST/fuzz/redteam yang diizinkan
        |
  catat PASS / FAIL / NOT-RUN / NOT-VERIFIED / N/A
        |
  FAIL sebelumnya? -- ya --> retest terikat + defect ID sama
        |                             |
  validasi lineage dan pencatatan <-+
        |
  defect terbuka -> BLOCKED; PASS cocok -> review closure
```

## Apakah struktur proses sebelumnya berubah?

Menambah gate pencatatan hasil dan kesinambungan riwayat kegagalan. Batas pengujian keamanan, restriksi perubahan produk dan persetujuan rilis tetap berlaku.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: uji IDOR A gagal; pengujian berikutnya tidak dapat dijalankan. NOT-RUN tidak menutup A. Sesudah perbaikan, retest PASS yang terikat dapat menutup defect.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/verify/security_ledger.py --plan <plan.json> --ledger <results.jsonl> --require-complete
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `.agent/runbooks/security-testing.md`
- `.agent/runbooks/security-verification.md`
- `scripts/verify/security_ledger.py`
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
