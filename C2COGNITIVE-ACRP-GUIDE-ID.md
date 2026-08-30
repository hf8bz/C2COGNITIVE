# C2Cognitive ACRP  -  Panduan Bahasa Indonesia

**C2Cognitive v1.0.0  |  Release 1  |  30 Agustus 2026**
**Author:** Hafizh Al-Banna

> **Status dokumentasi:** panduan publik yang bersifat explanatory. File ini tidak menggantikan `AGENTS.md`, `.agent/config.yml`, scope/runbook/schema current, prompt pintu masuk, atau validator executable. Jika prose bertentangan dengan kontrak executable, kontradiksi harus disurfacing dan kontrak kanonik tetap menjadi authority.

[Mulai dokumentasi](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Referensi](C2COGNITIVE-REFERENCE.md)  |  [Peta file](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Tujuan

Menjelaskan bagaimana C2Cognitive dapat mengoptimalkan representasi semantic set yang sudah di-admit ke model
tanpa mengubah membership evidence, trust, freshness, write authority, atau makna completion.

### Sumber implementasi kanonik

- [84-context-representation-planner.md](.agent/runbooks/context-representation.md)
- [context-representation.schema.md](.agent/context-representation.schema.md)
- [context-representation.md](.agent/runbooks/context-representation.md)
- [model-adapter.md](.agent/runbooks/model-adapter.md)

---

## Posisi di pipeline cognition

ACRP berada setelah semantic selection kanonik:

```text
repository / governed memory / verified Skill / structural candidate
                    |
                    v
        trust + ACL + freshness + evidence checks
                    |
                    v
          freeze semantic selection berurutan
                    |
                    v
                   ACRP
                    |
                    v
          model-adapter effective route
                    |
                    v
                    LLM
```

Representation optimization tidak boleh menambah record baru setelah selection dibekukan. Admission dan representation
adalah keputusan berbeda.

## Mode runtime

Kontrak Version 1 menyediakan safe native path dan representasi bounded sesuai profile/plan schema current.
Transformasi harus tetap mengikuti binding yang dipersyaratkan dan tidak boleh menciptakan evidence baru.

Productivity signal tidak boleh dipakai untuk:

- memasukkan memory yang gagal ACL/freshness;
- mempromosikan Skill yang belum verified;
- memperlebar Goal atau `ACTUAL_WRITE_SET`;
- menjadikan cache telemetry sebagai correctness evidence;
- atau mengklaim completion.

## Failover

Pergantian effective route dapat membatalkan kecocokan profile lama. Jika profile baru tidak dapat dibuktikan
compatible, gunakan native/default representation. Alias fisik hanya boleh memakai profile yang sama jika canonical
capability identity tetap berada dalam boundary yang verified; cache identity provider tetap terisolasi.

## Non-interference authority

```text
mode ACRP             != membership evidence
productivity ACRP     != correctness
compression ACRP      != izin write
route/cache telemetry != durable cognitive truth
```

## Verifikasi

```text
<C2PY> scripts/verify/context_representation.py
<C2PY> scripts/selftest/context_representation.py
<C2PY> scripts/selftest/fullstack_interactions.py
```

Resolusi `<C2PY>` dijelaskan di [C2COGNITIVE-CLI-LAUNCHER-GUIDE.md](C2COGNITIVE-CLI-LAUNCHER-GUIDE.md).

## Batas klaim

PASS hanya mendukung kontrak representation yang diuji. Ia tidak membuktikan cache hit provider, peningkatan reasoning
universal, atau equivalence semua model family.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
