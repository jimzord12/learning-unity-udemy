---
name: unity-script-review
description: Reviews the learner's Unity C# scripts against a three-tier checklist (must-fix, style, stretch) for Unity 6.6 and C# 9, labelling each remark as course shortcut or production practice. Use when asked to "review my script", "is this good Unity code", "why is Update slow", or before a commit that touches .cs files.
---

# Unity script review

Review as a coach: the learner should be able to fix each item themselves. Point at the line and the principle; ask "what do you think happens here?" before giving the fix. Full rewrite only on "show me".

## Tier 1: must-fix (correctness, version, performance)
- Compiles under **C# 9.0** (no file-scoped namespaces, `required`, raw strings, record structs, collection expressions, primary constructors).
- No `UnityEngine.Input` here (project is new-Input-System only); no removed shortcuts (`.rigidbody`, `.camera`...); `linearVelocity` not `velocity`; `Find*ByType` not `FindObjectOfType`.
- Domain reload is off: statics, static events and singletons are reset or unsubscribed (`OnDisable`).
- No scene searches (`Find*`, `GetComponent`, `Camera.main` in older Unity) inside `Update`; `GetComponent` cached in `Awake`.
- No per-frame allocations, LINQ or string concatenation in `Update`/`FixedUpdate`/`LateUpdate`.
- Physics work in `FixedUpdate`; movement scaled by `Time.deltaTime` where needed.
- `UnityEngine.Object` null-checked with `== null` or implicit bool, not `?.`/`??`.
- Events subscribed in `OnEnable`/`Awake` are unsubscribed in `OnDisable`/`OnDestroy`.
- Every new asset has its `.meta` committed alongside it.

## Tier 2: style
- PascalCase types/methods/properties; camelCase locals/params; `_camelCase` private fields; verb-prefixed bools.
- `[SerializeField] private`, not public fields; one MonoBehaviour per file named after its class; always braces.
- `CompareTag`, not string `==`. `[RequireComponent]` where a dependency is hard. `[Header]`/`[Tooltip]` on Inspector fields.
- Comments explain *why*, not what.

## Tier 3: stretch (only when the learner is ready)
- Decoupling with C# events / ScriptableObject channels; object pooling via `UnityEngine.Pool` **only after** a Profiler capture shows a spawn/GC cost.
- State machine when an `if` chain grows past ~3 states (heuristic).
- `Awaitable` vs coroutines (never await an `Awaitable` twice).

## Output format
For each remark: `[Tier N][course shortcut | production practice] file:line - principle - guiding question`. Keep to the top 3-5 remarks; don't flood a beginner.

Singletons are contested: flag, explain trade-offs (Awake order, duplicates, domain reload off), don't ban.
