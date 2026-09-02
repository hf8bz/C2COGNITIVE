# C2Cognitive C2PY Launcher Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Define the host-neutral notation used by C2Cognitive documentation for invoking shipped Python CLIs without
assuming that the executable is literally named `python3`.

### Canonical implementation sources

- [c2python.sh](scripts/c2python.sh)
- [c2python.cmd](scripts/c2python.cmd)
- [config.yml](.agent/config.yml)
- [prefix.lock](.agent/prefix.lock)

---

## `<C2PY>` is notation

When a guide says:

```text
<C2PY> scripts/verify/links.py
```

`<C2PY>` is not a shell variable and not a command named `C2PY`. It means **invoke the shipped C2Cognitive launcher
for the current host**.

## POSIX

Canonical launcher:

```sh
/bin/sh scripts/c2python.sh scripts/verify/links.py
```

`scripts/c2python.sh`:

1. honors `C2COGNITIVE_PYTHON` when it names an executable/path that satisfies the minimum runtime;
2. otherwise tries `python3`;
3. then `python`;
4. requires Python >= 3.8;
5. disables bytecode emission for the launched process.

## Windows cmd.exe

```bat
scripts\c2python.cmd scripts
erify\links.py
```

The launcher checks `C2COGNITIVE_PYTHON`, then `py -3`, `python`, and `python3`, requiring Python >= 3.8.

## Windows PowerShell

Use the command script explicitly, for example:

```powershell
& .\scripts\c2python.cmd scripts
erify\links.py
```

## Session restart rule

Resolve the launcher again after a host/CLI/session transition. Do not assume that a runtime path, virtual
environment, shell quoting rule, or environment variable from the previous session still applies.

## `C2COGNITIVE_PYTHON`

The environment variable is an executable/path only. Do not embed arbitrary command arguments inside it. The launcher
validates that the configured executable supports the minimum Python version.

## Failure semantics

Launcher failure is a runtime capability problem. It does not authorize silently switching to an unrelated interpreter
or modifying the repository to install Python. Report the capability gap and apply the matching blocker/budget rules.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
