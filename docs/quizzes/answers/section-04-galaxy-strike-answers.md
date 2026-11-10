# Section 04 answers (check only after you attempted each question)

1. A Timeline asset sequences animation, audio, activation and custom clips over time; a `PlayableDirector` component on a GameObject plays it. A **Signal**: a Signal Emitter marker on a Signal Track fires a named Signal asset at a time; a `SignalReceiver` component reacts (calls a method via UnityEvent), e.g. to show dialogue.
2. A value that changes over a normalized time/input range. Besides animation: easing, damage falloff, difficulty ramps, camera shake strength.
3. `Vector3 p = transform.localPosition; p.x = Mathf.Clamp(p.x, -5f, 5f); transform.localPosition = p;`. `Vector3` is a struct: you get a copy, so you must modify the copy and assign it back.
4. `2.5`. `Mathf.Lerp` clamps `t` to 0-1, so `Lerp(0, 10, 2)` returns `10`. (`LerpUnclamped` doesn't clamp.)
5. `Quaternion.Slerp` / `Quaternion.Lerp` / `Quaternion.RotateTowards`, or `Quaternion.Euler`, `LookRotation`. Quaternion components are not angles; editing them directly gives wrong rotations (Unity's docs advise against it).
6. `emission` returns a *struct* (a copy of the module), so changing a field of the returned value can't affect the particle system. Fix: `var emission = ps.emission; emission.enabled = true;`.
7.
   ```csharp
   [SerializeField] ParticleSystem[] lasers;
   void SetLasers(bool on)
   {
       foreach (ParticleSystem laser in lasers)
       {
           var emission = laser.emission;
           emission.enabled = on;
       }
   }
   ```
8. `enemy - player = (3,0,4)`. Length `5`. Normalise with `.normalized` (or `Vector3.Normalize`) to get `(0.6, 0, 0.8)`.
9. Screen pixel coordinates -> a world-space point. `z` is the distance from the camera along its forward direction; with z = 0 you get the camera's own position. (With the new Input System, get the mouse via `Mouse.current.position.ReadValue()`.)
10. A **nested prefab** is a prefab placed inside another prefab (reuse parts). A **prefab variant** inherits another prefab but overrides some values (e.g. enemy ship types sharing a base). The enemy ships were variants.
11. A Tag is a string label for identifying objects; a Layer is a numbered category used for physics collision matrix, camera culling masks, raycast masks, and which Volume/light affects it (post-processing layers).
12. Serialized reference (drag in the Inspector) is simplest and clearest. `FindFirstObjectByType` is OK once in `Awake/Start` and cached. Singleton is convenient but global and contested. Never call a `Find...` method in `Update`.
13. A method returning `IEnumerator` that can pause with `yield return`. `IEnumerator Reload() { yield return new WaitForSeconds(2f); SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex); }` started with `StartCoroutine(Reload())`. If the GameObject is destroyed or deactivated the coroutine stops.
14. `void Awake() { if (Instance != null && Instance != this) { Destroy(gameObject); return; } Instance = this; DontDestroyOnLoad(gameObject); }`. With **domain reload off**, statics survive between Play sessions: ordinary static values (counters, lists, events) are not reset; a static reference to a destroyed Unity object compares as `null`, but other static state is stale. Reset in a `[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.SubsystemRegistration)]` method.
15. (1) A **Volume** (global, or local with a collider) is in the scene and its **Layer** is in the camera's Volume Mask; (2) the Volume has a **Volume Profile** with overrides enabled; (3) the **Camera's Post Processing** checkbox is ticked (URP). Also check your URP renderer asset.
16. If missing: Window > Package Manager > Timeline (it's a core package in recent Unity 6 lines; your manifest doesn't list it, so check whether the window exists). TextMeshPro is merged into uGUI 2.x; keep `using TMPro;`.

**Rebuild challenge hints:** Input actions, `Mathf.Clamp` with copy-back, `ParticleSystem.emission` struct copy, collision/trigger with Rigidbody, public method for hits, serialized reference to the score UI.
