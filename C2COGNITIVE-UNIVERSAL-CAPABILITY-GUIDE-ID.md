# C2Cognitive | Perutean Kapabilitas Universal

**Versi:** 1.1.19 (kandidat publikasi)  
**Author:** Hafizh Al-Banna  
**Document class:** Panduan publik fitur dan proses

> Dokumentasi penjelas, bukan otoritas eksekusi atau laporan pengujian. `AGENTS.md`, Goal aktif, kontrak `.agent`, izin host dan source code terkini tetap mengatur.

## Apa yang berubah pada workflow sebelumnya

**Jenis integrasi:** Perluasan perencanaan bersyarat.

**Jalur sebelumnya:** Operator memilih runbook domain dari Goal aktif dan konteks repositori terkait. Gate tata kelola yang lama tetap menentukan apakah implementasi boleh berjalan.

**Pemicu baru:** Goal menyentuh kapabilitas aplikasi tertentu, keluarga industri yang belum dikenal, atau proses bisnis lintas modul.

## Alur proses dari awal sampai akhir

1. Baca Goal yang sudah diterima, requirement dan source terkini. Kenali perilaku nyata; jangan menebaknya dari label industri.
2. Jalankan pemilih read-only dengan argumen `--capability`, `--family`, `--module` atau `--archetype` yang eksplisit. `--summary` menyediakan discovery terbatas.
3. Pemilih memvalidasi identifier tepat, melengkapi dependensi yang dinyatakan dan mengembalikan daftar path runbook terbatas.
4. Baca hanya runbook terpilih dan konfirmasi setiap dependensi hasil inferensi terhadap proyek dan pemiliknya.
5. Ikat kapabilitas terpilih ke aktor, tenant, transisi, oracle independen, kasus negatif dan kebijakan proyek.
6. Teruskan obligation ke Goal, perencanaan exact-write, dan gate application assurance yang sudah ada; hasil pemilih bukan otoritas.

### Keputusan / berhenti / pemulihan

Pilihan dapat berstatus `ADVISORY_ONLY` dan `BLOCKED_PENDING_PROJECT_EVIDENCE`; tidak otomatis terjadi edit produk, keberhasilan eksekusi atau klaim kepatuhan.

## Diagram proses

```text
Goal + requirement nyata
        |
  ID kapabilitas eksplisit
        |
  pemilih read-only
        |
  ID valid? -- tidak --> TOLAK
        | ya
  closure dependensi terbatas
        |
  runbook terpilih (ADVISORY_ONLY)
        |
  bukti proyek tersedia? -- tidak --> BLOCKED
        | ya
  gate exact-write/QA lama
```

## Apakah struktur proses sebelumnya berubah?

Menambah jalur on-demand sebelum perencanaan berskop. Tidak mengganti `AGENTS.md`, mengubah Core rules, atau mewajibkan seluruh 58 family / 19 kontrak universal.

| Batas | Dampak |
|---|---|
| `Goal aktif` | Tetap menjadi sumber pekerjaan terotorisasi; panduan tidak membuat Goal. |
| `CORE / AGENTS.md` | Invariant dan routed scopes lama tetap lebih tinggi otoritasnya. |
| `Exact write set` | Tetap diperlukan sebelum mutasi nyata produk/repository. |
| `Approval dan rollback` | Tetap persyaratan independen untuk perubahan sensitif. |
| `Fitur tidak dipilih` | Tidak otomatis menjadi pekerjaan aktif atau cakupan global. |
| `Verifikasi` | Dapat memperketat acceptance yang relevan; hasil sintetis tidak menggantikan eksekusi nyata. |

## Skenario ilustratif

Contoh: layanan janji temu kustom memilih `scheduling-capacity` dan `temporal-effective-backdate` hanya jika requirement memuat perilaku itu; aturan legal HRIS atau ERP tidak ikut diwariskan.

## Contoh entry read-only / terbatas

```sh
python3 -B scripts/domain/universal.py --project-type custom --capability temporal-effective-backdate
```

Jalankan hanya setelah memeriksa source dan prasyarat terpasang. Input tanda kurung sudut adalah placeholder, bukan nilai siap eksekusi.

## Referensi implementasi di distribusi

- `.agent/runbooks/application-domain-router.md`
- `docs/UNIVERSAL-CAPABILITY-PROTOCOL.md`
- `scripts/domain/universal.py`
- `.agent/capability-registry.json`

## Batasan dan perilaku saat gagal

- `Unknown` bukan `false`; obligation yang relevan dan belum terpenuhi tetap menjadi blocker.
- Panduan tidak mengautentikasi approval atau membuktikan ketersediaan provider.
- Fixture sintetis bukan pengujian aplikasi produksi.
- Berhenti atau suspend dengan blocker bernama jika prasyarat, scope, bukti atau budget kurang.
- Catatan versi lama dan evidence rilis adalah provenance, bukan bukti kompatibilitas terkini.

## Dokumentasi terkait

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
