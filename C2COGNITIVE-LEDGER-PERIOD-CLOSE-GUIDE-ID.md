# C2Cognitive | Assurance Ledger, Rekonsiliasi, dan Tutup Periode

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Jalur assurance khusus kapabilitas.

**Jalur sebelumnya:** Gate exact-write dan verifikasi umum tetap berlaku, tetapi pemeriksaan kode saja tidak cukup untuk tanggal efektif bisnis dan invariant siklus akuntansi.

**Pemicu baru:** Aplikasi mempunyai posting keuangan, pembalikan jurnal, event tertunda, kebijakan akuntansi, rekonsiliasi saldo, backdating, atau periode terkunci.

## Alur proses dari awal sampai akhir

1. Identifikasi entitas, ledger, pemilik kebijakan, aktor posting, mata uang dan batas periode dari aturan proyek.
2. Pisahkan waktu event/transaksi, waktu efektif bisnis, waktu pencatatan dan waktu posting. Pertahankan makna query historis as-of.
3. Modelkan status open, soft-closed, closed dan reopened hanya jika didukung; tentukan pihak yang berwenang menyetujui penyesuaian atau pembukaan kembali.
4. Tentukan oracle independen untuk keseimbangan, immutability entri posted, idempotensi, reversal dan aturan period-lock.
5. Uji aktor yang diizinkan/ditolak, duplikasi/retry, event tidak berurutan, settlement parsial, penyesuaian bertanggal mundur dan transisi close/reopen.
6. Petakan invariant dan pengecualian rekonsiliasi yang belum selesai menjadi blocker assurance. Perubahan posting tetap membutuhkan Goal dan exact-write authority.

### Keputusan / berhenti / pemulihan

Tidak ada runbook generik yang boleh menciptakan tarif pajak, hukum payroll, atau kebijakan periode. Pada periode tertutup, aksi (reject, adjustment, reversing entry atau reopen) harus berasal dari kebijakan proyek.

## Diagram proses

```text
Event bisnis + kebijakan akuntansi
        |
  klasifikasikan waktu event/efektif/posting
        |
  periode OPEN? -- tidak --> adjustment/reject/reverse sesuai kebijakan
        | ya                       |
  posting idempoten             keputusan kebijakan
        |                          |
  pemeriksaan balancing & rekonsiliasi independen
        |
  unverified? -> BLOCKED; verified -> review completion Goal
```

## Apakah struktur proses sebelumnya berubah?

Memperdalam jalur QA/Goal lama pada aplikasi yang berkapabilitas akuntansi; bukan ledger, scheduler, atau mesin akuntansi baru yang selalu berjalan.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: pembayaran masuk sesudah bulan ditutup. Workflow melihat kebijakan proyek; tidak boleh diam-diam mengedit jurnal tertutup agar rekonsiliasi lolos.

## Referensi implementasi di distribusi

- `.agent/runbooks/accounting-policy-profile.md`
- `.agent/runbooks/ledger-invariants.md`
- `.agent/runbooks/period-close.md`
- `.agent/runbooks/reconciliation-and-recovery.md`
- `.agent/runbooks/capabilities/temporal-effective-backdate.md`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
