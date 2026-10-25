# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

This folder is a documentation project about one noise problem: rooftop units at 999 W. Big Beaver Rd, Troy, MI. It has no code, build, or test system. The parent repo's CLAUDE.md applies here too, including the markdownlint and no-hard-wrap rules.

## Commands

Lint all files (run from this folder):

```bash
markdownlint --fix --config ~/.markdownlint.json *.md
```

Check that every `[[name]]` wiki-link resolves to a file in this folder:

```bash
grep -o "\[\[[^]]*\]\]" *.md | sed 's/.*\[\[//;s/\]\]//' | sort -u | while read n; do [ -f "$n.md" ] || echo "MISSING: $n"; done
```

No output means every link resolves.

## Structure

The folder is flat on purpose. Each file has one role:

- **Reference** (facts, change rarely): `problem_and_owner.md`, `law.md`, `contacts.md`, `supporting_screed.md`, `shared_notes.md`.
- **Actions** (what to do, what's been done): `calls.md`, which holds priorities, blockers, and the call log; `poster_distribution.md`, which holds apartment buildings by distance and posting steps.
- **Artifacts** (sent or posted): `scripts.md`, `poster.md`, `image_prompt.md`, and `images/`.
- `README.md` is the index and status. Update its Status section when something happens.

## Conventions

- **Phone numbers and emails live only in `contacts.md`.** Scripts and the poster repeat a number only where it's printed for a reader. When a number changes, update `contacts.md` first, then the copies.
- **Log every call in the Log section of `calls.md`.** Use the system clock time (`date`), and mark anything that's from the user's own report.
- **Placeholders are `[UPPER_CASE]`** (for example `[NAME]`, `[CODE ENFORCEMENT EMAIL]`). Don't fill them with guesses.
- **`supporting_screed.md` is not for calls, email, or posting.** Scripts and the poster use only facts and requests from it.
- **Use the common meaning of "trespass" in conversation only.** Don't write "trespass" or "assault" in scripts, the poster, or any record. Michigan law treats noise as private nuisance; see `law.md`.
- **Don't add more invite links.** `shared_notes.md` already holds one that was pushed to the remote.
- **Unverified facts stay marked as unverified** (for example the QFC precedent in `problem_and_owner.md`, or the 2014-era Chapter 88 text in `law.md`).

## Limits

Claude cannot place calls or send email. The user does that and reports back, and the log is updated from the user's report.
