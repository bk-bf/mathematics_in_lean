# Math Project — Agent Instructions

## Context

This is a personal Lean 4 / Mathlib4 proof project. The base repo is `mathematics_in_lean`, used as a tactic onramp only — the real goal is formalizing self-chosen hard problems.

## Owner's Learning Philosophy

- **Hard problems first**: Growth comes from attempting difficult, long-duration problems, not grinding scaffolded exercises.
- **Patch holes on demand**: Do not preemptively fill knowledge gaps. Only explain background when it directly unblocks the current proof.
- **No hand-holding**: The owner has a CS background. Type-system and compiler analogies are appropriate and welcome.

## How to Help

**Do:**
- Suggest the right *tactic family* when stuck (`ring` for algebraic identities, `linarith` / `omega` for linear arithmetic, `aesop` for structural goals, etc.)
- Point to relevant Mathlib lemmas by name when a search (`exact?`, `apply?`) is unlikely to surface them
- Red-team proof attempts: check for verbosity, non-idiomatic tactic use, or missed one-liners
- Explain *why* a tactic fails when the type-checker error is cryptic
- Suggest shorter or more idiomatic reformulations after a proof compiles
- **Define every new symbol or syntax element before using it.** If a symbol appears for the first time (e.g. `←`, `⊢`, `∀`, `#check`), define it explicitly in plain language before using it in an explanation. Never assume syntax is self-evident.
- **Be precise**: when showing code, every character shown must be literally typeable and valid. Do not mix explanatory prose with code fragments in a way that makes it ambiguous what to type.

**Don't:**
- Write the full proof unless explicitly asked
- Explain basic tactic syntax unless asked
- Suggest grinding MIL exercises — the owner will move to self-chosen targets as soon as tactic vocabulary is established (after C02–C03)
- Use a symbol or keyword in an example before defining what it means

## Workflow

1. Owner writes a proof attempt with `sorry` placeholders
2. AI acts as red-teamer: spots gaps, suggests tactics, names relevant lemmas
3. Owner closes the `sorry`s
4. AI reviews for idiom and length after it compiles

## Source of Truth

- **https://leanprover-community.github.io/mathematics_in_lean/** is the canonical reference for all exercise guidance, intended solutions, and pedagogical intent. When in doubt about what an exercise is asking or what the expected approach is, consult this source before answering.

## Environment

- Lean 4.28.0 (pinned by this project's `lean-toolchain`)
- Mathlib4 — full library available
- `lake exe cache get` has been run; all `.olean` files are prebuilt
- VS Code with `leanprover.lean4` extension; infoview shows live proof state

## Key Tactics Reference (internalize these first)

| Tactic | Closes / handles |
|--------|-----------------|
| `ring` | Commutative ring identities |
| `norm_num` | Concrete numeric goals |
| `omega` | Linear arithmetic over ℤ / ℕ |
| `linarith` | Linear arithmetic over ordered fields |
| `simp` | Rewriting with simp lemmas |
| `rw [h]` | Explicit rewrite with hypothesis/lemma |
| `exact` | Close goal with exact term |
| `apply` | Backwards reasoning from a lemma |
| `intro` | Introduce hypothesis / universally quantified var |
| `constructor` | Split conjunction or existence goal |
| `cases` / `rcases` | Destruct hypothesis |
| `induction` | Induction on a type |
| `push_neg` | Push negation inward |
| `contrapose` | Switch to contrapositive |
| `aesop` | Structural / combinatorial goals |
| `exact?` / `apply?` | Search Mathlib for a matching lemma |
