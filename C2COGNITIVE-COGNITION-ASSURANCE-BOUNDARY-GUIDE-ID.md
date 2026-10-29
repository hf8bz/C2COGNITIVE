# C2Cognitive | Batas Bukti Kognitif, Recall, dan Assurance

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Batas otoritas khusus C2Cognitive.

**Jalur sebelumnya:** Memory L0–L3, Skills, kandidat struktural, Wiki dan loadout sudah menyediakan konteks terbatas. Semuanya advisory, bukan verifikasi source terkini.

**Pemicu baru:** Agent jangka panjang me-recall fakta, lesson, Skill atau hasil Wiki lama saat merencanakan assurance atau implementasi baru.

## Alur proses dari awal sampai akhir

1. Tentukan Goal dan source saat ini, lalu minta recall terbatas dengan filter ACL dan freshness yang sudah ada.
2. Perlakukan hit sebagai penunjuk; periksa ulang evidence pendukung dan hash source, lifecycle, visibility dan persyaratan confidence.
3. Keluarkan objek stale, retired, superseded, tidak didukung atau tidak boleh diakses dari konteks aksi normal.
4. Gunakan record yang lolos untuk mengusulkan profil kapabilitas, risiko dan skenario uji independen, bukan menyatakan kepatuhan proyek.
5. Jalankan application assurance terhadap repositori dan environment nyata yang terkini; Goal dan exact write set tetap mengatur mutasi.
6. Jika klaim memory bertentangan dengan bukti baru, catat koreksi atau retire memory tergantung lewat lifecycle yang sah; confidence recall tidak boleh melewati blocker.

### Keputusan / berhenti / pemulihan

Memory tidak dapat memenuhi obligation assurance hanya karena ada. Bukti terikat source dan eksekusi yang dibutuhkan tetap harus tersedia secara independen.

## Diagram proses

```text
Goal/source terkini + recall memory terbatas
        |
  filter ACL / freshness / lifecycle / support
        |
  stale/tak bisa diakses? -- ya --> KELUARKAN / retire via lifecycle
        | tidak
  hanya usulan / kandidat tes
        |
  bukti baru khusus aplikasi
        |
  gate assurance nyata + write authority kanonis
```

## Apakah struktur proses sebelumnya berubah?

Menggabungkan jalur capability/assurance baru dengan cognition plane lama; tidak mengubah memory, Wiki, Skill atau provider cache menjadi otoritas kanonis.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: pengujian integrasi pembayaran pernah hijau sebelum webhook handler berubah. Lesson lama dapat menunjukkan lokasi tes, tetapi eksekusi baru dan bukti terikat source tetap wajib.

## Referensi implementasi di distribusi

- `.agent/runbooks/memory-lifecycle.md`
- `scripts/memory/core.py`
- `scripts/wiki/build.py`
- `scripts/assurance/application.py`
- `AGENTS.md`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
