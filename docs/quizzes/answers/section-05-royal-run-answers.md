# Section 05 answers (check only after you attempted each question)

1. `for` when you know the count (or have an index); `while` when you loop until a condition changes. `for (int i = 0; i < 5; i++) { Instantiate(chunkPrefab, new Vector3(0, 0, i * 10f), Quaternion.identity); }`
2. A list resizes: `Add`, `Insert`, `Remove`, `RemoveAt`, `Contains`. An array has a fixed size. `List.Count` vs array `Length`.
3. `[B, C]`, `Count` 2. Modifying a collection while enumerating it invalidates the enumerator, so `foreach` throws `InvalidOperationException`. Loop backwards by index, or collect then remove.
4. `1`. Uses: every Nth thing (every 4th checkpoint), wrapping an index (`i % count`), alternating (`i % 2 == 0`).
5. `int lane = Mathf.RoundToInt(x / 2f) + 1;` (clamp to 0-2 with `Mathf.Clamp`).
6. Friction and bounciness of colliders. Combine (Average, Minimum, Multiply, Maximum) decides how two colliders' values merge. In Unity 6 the class is `PhysicsMaterial` (it was `PhysicMaterial`); verify in the 6000.6 script reference.
7. `virtual`: base provides a default implementation that derived classes may `override`. `abstract`: no implementation in the base, derived classes **must** override (abstract class can't be instantiated).
8. A property controls access (read anywhere, write only inside), can validate or react to changes, and lets you change the implementation without changing callers.
9. In Unity 6.3+ `[SerializeField]` on a property is a **compile error**. Use `[field: SerializeField] public int Score { get; private set; }`.
10. Pass the reference in rather than the object looking it up: a serialized field, or an `Init(ScoreManager sm)` call by whoever spawns it. Explicit dependencies, no hidden search cost, easy to see and change.
11. Trigger = one-shot event (hit, jump); Bool = persistent state (isRunning); Float/Int = continuous values (speed). `StringToHash` caches the parameter ID as an int, avoiding repeated string lookups.
12. Movement scaled by `Time.deltaTime` stops (deltaTime is 0). Animation using **unscaled** time keeps running. `Update()` still gets called every frame; only time-scaled logic stops.
13. `timeLeft -= Time.deltaTime; timeLeft = Mathf.Max(timeLeft, 0f); if (timeLeft <= 0f) { GameOver(); }` (guard GameOver so it only runs once).
14. They improve the Inspector: `[Header("Movement")]` adds a heading; `[Tooltip("...")]` shows hover help on that field.
15. Cinemachine **Impulse Source** (generate the impulse, `GenerateImpulse()`) and **Impulse Listener** (on the camera). Cinemachine 3 differs from older videos: check `docs.unity3d.com/Packages/com.unity.cinemachine@<installed version>/manual/` (Cinemachine isn't in your manifest yet).

**Rebuild challenge hints:** `for` loop spawning, `List<GameObject>`, `RemoveAt(0)` after destroy, `Mathf.Clamp` lanes, a base `Pickup` + derived classes, `[field: SerializeField]` properties.
