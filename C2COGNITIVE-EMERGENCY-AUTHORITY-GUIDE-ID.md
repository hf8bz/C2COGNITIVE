# C2Cognitive Emergency Authority  -  Panduan Bahasa Indonesia

**C2Cognitive v1.0.0  |  Release 1  |  30 Agustus 2026**
**Author:** Hafizh Al-Banna

> **Status dokumentasi:** panduan publik yang bersifat explanatory. File ini tidak menggantikan `AGENTS.md`, `.agent/config.yml`, scope/runbook/schema current, prompt pintu masuk, atau validator executable. Jika prose bertentangan dengan kontrak executable, kontradiksi harus disurfacing dan kontrak kanonik tetap menjadi authority.

[Mulai dokumentasi](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Referensi](C2COGNITIVE-REFERENCE.md)  |  [Peta file](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Tujuan

Menjelaskan dua authority plane darurat yang shipped: Cognitive Emergency Authorization (CEA) dan Bounded
Emergency Authority (BEA), serta aturan bahwa keduanya independent, exact, expiring, dan bukan wildcard
permission.

### Sumber implementasi kanonik

- [emergency-authority.schema.md](.agent/emergency-authority.schema.md)
- [bounded-emergency-authority.schema.md](.agent/bounded-emergency-authority.schema.md)
- [emergency-authority.md](.agent/runbooks/emergency-authority.md)
- [bounded-emergency-authority.md](.agent/runbooks/bounded-emergency-authority.md)
- [emergency](scripts/emergency/)

---

## Dua plane terpisah

| Plane | Tujuan | Authority |
| --- | --- | --- |
| CEA | containment/purge persistent cognition terdampak | exact cognitive effects; tidak memberi product write |
| BEA | emergency repository repair | exact forward repository writes; tidak memberi CEA authority |

Jika keduanya dibutuhkan, obtain dua grant terpisah.

## Properti bersama

Human-granted di host, exact binding, exact action/target, TTL/expiry, auditable, non-wildcard, revocable/auto-expire,
dan tidak bypass unrelated semantic scope.

## CEA

Lihat [C2COGNITIVE-CEA-GUIDE.md](C2COGNITIVE-CEA-GUIDE.md). CEA-CONTAIN monotone-restrictive; CEA-PURGE adalah jalur
exceptional yang lebih kuat.

## BEA

BEA adalah overlay pada exact repository-write plan. Ia tidak mengizinkan vague directory, unknown future mutation,
atau rollback bypass. ACRP/cache/routing tidak memperlebar scope BEA.

## Host approval

Repository memvalidasi grant contract; host mengautentikasi human approver dan mengisolasi approval/check endpoint.
Local grant bukan cryptographic identity signature kecuali memang ada signing system eksternal.

## Emergency tetap diverifikasi

Contain/authorize -> exact effect -> verify -> expire/revoke. Target baru harus kembali ke proposal/planning.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
