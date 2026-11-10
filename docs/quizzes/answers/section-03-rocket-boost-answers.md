# Section 03 answers (check only after you attempted each question)

1. `AddForce` uses **world** directions; `AddRelativeForce` uses the object's **local** axes. For thrust along the rocket's own nose use `rb.AddRelativeForce(Vector3.up * thrust * Time.deltaTime);` (or whichever local axis is the nose).
2. If both your rotation and physics act, they fight (spinning after a collision). So set `rb.freezeRotation = true` while you rotate manually, then `false` again so physics works.
3. Asset -> Action Maps (e.g. Player) -> Actions (e.g. Move, Fire) -> Bindings (keys/buttons). In code: `InputAction.ReadValue<float>()` (or `Vector2`). The action must be **enabled** (`action.Enable()` or via `PlayerInput`/`InputActionReference` handling) or it reads nothing. Search: `unity input system InputActionReference ReadValue`.
4. A namespace groups type names so they don't clash. `using UnityEngine;` lets you write `Rigidbody` instead of `UnityEngine.Rigidbody`. A MonoBehaviour's class name must match its file name so Unity can link the script asset to the class.
5.
   ```csharp
   switch (tag)
   {
       case "Friendly": Debug.Log("ok"); break;
       case "Finish": LoadNext(); break;
       default: Crash(); break;
   }
   ```
6. The scene must be in the **build scene list** (File > Build Profiles > Scene List in Unity 6) with the index you used. Also check the index/spelling.
7. `int next = SceneManager.GetActiveScene().buildIndex + 1; if (next == SceneManager.sceneCountInBuildSettings) { next = 0; } SceneManager.LoadScene(next);` (or `next % count`).
8. Calls the named method after 1 second. Downside: it's a string, so typos or renames fail silently/at runtime. Alternatives: a coroutine with `WaitForSeconds`, or `Awaitable`. Using `nameof(ReloadLevel)` removes typos.
9. `AudioSource` plays sound from an object; `AudioClip` is the audio file; `AudioListener` is the "ears" (normally on the camera; only one active). `PlayOneShot(clip)` layers sounds without cutting off the current one; `Play()` restarts the source's single clip.
10. `if (!audioSource.isPlaying) { audioSource.PlayOneShot(thrustClip); }` (and `Stop()` when the key is released if you use `Play`).
11. It stops the crash/success code running repeatedly (and stops input) while the delayed reload/next-level is pending.
12. -2 to +2. One cycle is 2π seconds (about 6.28 s). For 4 seconds: `Mathf.Sin(Time.time * (2f * Mathf.PI / 4f))`. (Remember to add the start position.)
13. **Domain reload is off** by default in new 6.6 projects, so static fields keep their value between Play sessions. Fix: reset statics at start of Play with `[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.SubsystemRegistration)]` on a static method that sets `deaths = 0`, or avoid statics (use an instance field), or re-enable domain reload in Project Settings > Editor > Enter Play Mode Settings.
14. In Unity 6 they are `linearDamping` and `angularDamping` (Inspector: **Linear Damping** / **Angular Damping**). Also `velocity` -> `linearVelocity`.

**Rebuild challenge hints:** `rb.AddRelativeForce`, `freezeRotation`, input action values, `isPlaying`, `SceneManager`, `Invoke` or a coroutine, reset statics, `linearDamping`.
