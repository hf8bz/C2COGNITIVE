# C2Cognitive  -  Progress Liveness & Bounded Self-Audit

**C2Cognitive v1.0.0  |  Release 1  |  30 Agustus 2026**
**Author:** Hafizh Al-Banna

> **Status dokumentasi:** panduan publik yang bersifat explanatory. File ini tidak menggantikan `AGENTS.md`, `.agent/config.yml`, scope/runbook/schema current, prompt pintu masuk, atau validator executable. Jika prose bertentangan dengan kontrak executable, kontradiksi harus disurfacing dan kontrak kanonik tetap menjadi authority.

[Mulai dokumentasi](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Referensi](C2COGNITIVE-REFERENCE.md)  |  [Peta file](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Tujuan

Mendokumentasikan liveness model yang membedakan tool activity dari evidence-backed semantic progress serta
recovery bounded ketika progress stagnan.

### Sumber implementasi kanonik

- [85-progress-liveness-self-audit.md](.agent/runbooks/progress-liveness.md)
- [progress.schema.md](.agent/progress.schema.md)
- [progress-liveness.md](.agent/runbooks/progress-liveness.md)
- [progress](scripts/progress/)
- [progress_liveness.py](scripts/verify/progress_liveness.py)

---

## Masalah

Process dapat sibuk tetapi tidak mendekati Goal. Tool call, message, retry, dan CPU activity bukan bukti progress yang
cukup.

## Tiga clock

Kontrak membedakan semantic progress, visible/host activity, dan externally justified wait agar long-running operation
yang valid tidak langsung dianggap stagnan.

## Progress frontier

Event dianggap progress hanya bila memajukan governed work-state component, bukan mengulang aktivitas.

## Trigger

1. klasifikasi semantic progress;
2. bedakan benign wait/long-running/accounting inconsistency dari stagnation;
3. bounded diagnostic fan-out bila perlu;
4. reduction;
5. recovery bounded;
6. verify frontier berubah.

## Authority boundary

Liveness finding tidak dapat membuat Goal, evidence, write authority, atau bypass human decision.

## Host-survival

Self-audit yang hanya hidup di process tidak boleh mengklaim survive process death. Resume lintas session menggunakan
handoff/resume contract.

## Verifikasi

Finite/synthetic PASS mendukung state space yang dimodelkan, bukan semua perilaku sistem eksternal.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
