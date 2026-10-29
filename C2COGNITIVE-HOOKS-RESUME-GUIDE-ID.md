# C2Cognitive | Batas Hook Compaction dan Resume

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Adapter host opsional dan pengaman continuity.

**Jalur sebelumnya:** Goal, HANDOFF/CURSOR dan terminal reconciliation yang sudah ada menjaga state jangka panjang. Event hook sendiri bukan sumber otoritas repositori.

**Pemicu baru:** Host yang sudah diverifikasi mendukung event compaction/session atau checkpoint manual diminta.

## Alur proses dari awal sampai akhir

1. Periksa host/versi/kontrak event dan konfigurasi tepat; file yang ada di disk belum tentu aktif.
2. Pilih hanya bridge yang cocok. Adapter OpenCode V1 dan V2 tidak boleh diaktifkan bersamaan.
3. Saat pekerjaan sudah diotorisasi, simpan Goal, HANDOFF/CURSOR, blocker, pointer bukti dan approval secara terbatas; hook tidak boleh menulis tiba-tiba.
4. Saat event diterima, bridge membaca state tepat dengan batas dan mengeluarkan teks advisory atau notifikasi degraded jika state hilang/tidak aman.
5. Sesudah compact/restart, jalankan rehydration normal, verifikasi source dan terminal truth terkini. Tolak cursor usang yang membuka run selesai.
6. Jika event native belum terverifikasi, gunakan checkpoint manual; sesi baru mewarisi Goal lama dan tidak menciptakan izin tulis.

### Keputusan / berhenti / pemulihan

Hook boleh memberi saran, tetapi tidak boleh menjalankan auto-compact sendiri, menyimpan handoff tanpa izin, memberi Goal baru, atau me-resume run terminal.

## Diagram proses

```text
Konfigurasi host valid + adapter sesuai
        |
  event native teramati? -- tidak --> checkpoint manual
        | ya                              |
  advisory terbatas                     |
        |                                |
  rehydrate HANDOFF / CURSOR kanonis <---+
        |
  terminal truth? -- COMPLETED --> tolak resume run sama
        | aktif
  validasi Goal/source/approval sebelum aksi
```

## Apakah struktur proses sebelumnya berubah?

Menambah integrasi host opsional di sekitar workflow continuity yang sudah ada. State machine kanonis dan otoritas tulis tidak berubah.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: host mengirim event compaction sesudah reload plugin. Bridge memberi notifikasi continuity terbatas; agent tetap memvalidasi HANDOFF dan source sebelum menulis.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/hooks/continuity.py --harness manual
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `.agent/runbooks/harness-hooks.md`
- `scripts/hooks/README.md`
- `scripts/hooks/continuity.py`
- `scripts/hooks/opencode.mjs`
- `scripts/hooks/opencode-v2.mjs`
- `scripts/handoff/terminal_reconcile.py`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
