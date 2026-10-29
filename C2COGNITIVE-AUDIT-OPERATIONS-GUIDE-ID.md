# C2Cognitive | Audit Otomatis Terbatas dan Gate Rilis

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Orkestrasi verifikasi rilis.

**Jalur sebelumnya:** Workflow verifikasi sebelumnya menguji perilaku yang dinyatakan dan melaporkan hasil tepat. Audit berulang tanpa perubahan bukan kemajuan semantik.

**Pemicu baru:** Kandidat rilis lokal memerlukan pemeriksaan source, docs, package atau resource yang deterministik dan terbatas.

## Alur proses dari awal sampai akhir

1. Bekukan identitas repositori, cakupan kandidat, daftar pemeriksaan, environment dan budget resource terbatas.
2. Jalankan pemeriksaan source/doc/link/diagram terbatas dan kasus mutasi negatif berbeda tiap putaran; berhenti pada kegagalan pertama.
3. Gunakan child process berurutan dengan batas waktu, memori dan output; tulis laporan audit di luar source.
4. Jika seluruh putaran terkonfigurasi lolos, jalankan gate snapshot/performance dan full selftest secara terpisah sesuai opsi.
5. Catat FAIL, unsupported atau NOT-RUN secara terpisah. Akses uji Android/web/cloud native yang tidak ada bukan verified.
6. Publikasikan hanya klaim yang ditopang kandidat tepat yang diuji. Laporan bukti tetap internal, bukan dalam panduan fitur publik.

### Keputusan / berhenti / pemulihan

Runner audit berulang menerima 11..25 putaran dan memerlukan Linux/WSL resource limits. PASS hanya berlaku untuk pemeriksaan lokal yang dinyatakan.

## Diagram proses

```text
Subjek dibekukan + jumlah putaran terbatas
        |
  pemeriksaan terbatas + kasus negatif berbeda
        |
  FAIL? -- ya --> stop / perbaiki lewat otorisasi lama
        | tidak
  masih ada putaran? -- ya --> putaran berbeda berikutnya
        | tidak
  gate resource/full-suite opsional
        |
  laporkan hasil lokal + batas NOT-RUN eksplisit
```

## Apakah struktur proses sebelumnya berubah?

Menambah jalur QA/rilis terbatas, bukan loop agent tanpa batas, reviewer independen, atau persetujuan rilis global.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: tautan dokumentasi lolos tetapi uji anggota ZIP berbahaya gagal. Kandidat tidak lulus; mengulang putaran yang sama tanpa memperbaiki penyebab bukan completion.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/quality/continuous_release_audit.py --root . --out <report-outside-repo.json> --rounds 11
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `scripts/quality/automated_release_audit.py`
- `scripts/quality/continuous_release_audit.py`
- `scripts/quality/run_resource_gates.py`
- `.agent/runbooks/workflow-convergence.md`
- `docs/application-assurance/AUDIT-AUTOMATION-DURABILITY.md`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
