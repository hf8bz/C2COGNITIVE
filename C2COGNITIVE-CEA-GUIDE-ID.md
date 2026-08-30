# C2Cognitive CEA  -  Panduan Bahasa Indonesia

**C2Cognitive v1.0.0  |  Release 1  |  30 Agustus 2026**
**Author:** Hafizh Al-Banna

> **Status dokumentasi:** panduan publik yang bersifat explanatory. File ini tidak menggantikan `AGENTS.md`, `.agent/config.yml`, scope/runbook/schema current, prompt pintu masuk, atau validator executable. Jika prose bertentangan dengan kontrak executable, kontradiksi harus disurfacing dan kontrak kanonik tetap menjadi authority.

[Mulai dokumentasi](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Referensi](C2COGNITIVE-REFERENCE.md)  |  [Peta file](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Tujuan

Menjelaskan emergency authority untuk containment atau purge persistent-cognition object yang terdampak tanpa
mewarisi repository/product write authority.

### Sumber implementasi kanonik

- [emergency-authority.schema.md](.agent/emergency-authority.schema.md)
- [emergency-authority.md](.agent/runbooks/emergency-authority.md)
- [cognitive_authority.py](scripts/emergency/cognitive_authority.py)
- [cognitive_effect.py](scripts/emergency/cognitive_effect.py)
- [memory-lifecycle.md](.agent/runbooks/memory-lifecycle.md)

---

## Scope CEA

- **CEA-CONTAIN**  -  action monotone-restrictive seperti retire memory/Skill terdampak, revoke worker/session path yang
  terdampak, atau invalidasi actionability Wiki sesuai kontrak exact.
- **CEA-PURGE**  -  approval lebih kuat untuk jalur exceptional `SECURITY_PURGE` yang sudah ada.

CEA **bukan** repository write authority.

## Flow

```text
DETECT
  v
DEFENSIVE SUPPRESSION
  v
EXACT AFFECTED OBJECT SET
  v
CEA PROPOSAL
  v
HUMAN APPROVAL DI HOST
  v
CANONICAL EFFECT
  v
DECLARED INVALIDATION / REVOCATION
  v
VERIFY
  v
EXPIRE / AUTO-REVOKE GRANT
```

Detection boleh suppress actionability tetapi tidak boleh memberi authority lebih kuat kepada dirinya sendiri.

## Exact binding

Proposal/grant terikat pada incident/run/session/Goal yang relevan, exact typed object, exact action, dan TTL.
Implementasi tidak mengklaim general dependency closure tanpa batas.

## CEA dan BEA terpisah

Jika incident memerlukan cognitive containment dan repository repair, authority-nya harus diperoleh terpisah. Tidak
ada inheritance antar-plane.

## Human approval

Package memvalidasi shape/binding; autentikasi human approver adalah tanggung jawab host. JSON grant lokal bukan
signature publisher identity.

## Batas klaim

CEA tidak membuktikan eradication dari semua external cache, provider state, backup, transcript, atau sistem di luar
governed C2Cognitive stores.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
