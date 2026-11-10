# Breaking changes relevant to older course code (to Unity 6000.6)

Confidence: "Official" = read on a Unity 6000.6 manual/script-reference/upgrade page during research. "Check" = not confirmed hard error vs warning; use the new name regardless. Always re-verify in the 6000.6 docs before asserting.

| Old (2019-2022 era) | Use now | Since | Confidence |
|---|---|---|---|
| `Rigidbody.velocity` | `linearVelocity` | 6.0 | Official (old name absent from 6000.6 reference; error vs warning: Check) |
| `Rigidbody.drag` / `angularDrag` | `linearDamping` / `angularDamping` | 6.0 | Same as above |
| `FindObjectOfType<T>()` | `FindAnyObjectByType<T>()` (any) or `FindFirstObjectByType<T>()` (deterministic) | 6.0 deprecated | Official (deprecated, still compiles) |
| `FindObjectsOfType<T>()` | `FindObjectsByType<T>(FindObjectsSortMode.None)` | 6.0 deprecated | Official |
| `gameObject.rigidbody`, `.camera`, `.light`, `.renderer`, `.audio`, `.collider`... shortcuts | `GetComponent<T>()` | removed 6.5 | Official |
| `AddComponent("Name")` (string) | `AddComponent<T>()` | removed 6.5 | Official |
| `GetInstanceID()` / int InstanceID APIs | `EntityId` / `GetEntityId()`; never cast to int | 6.5 | Official |
| `Input.GetAxis/GetKey/GetKeyDown/mousePosition` | Input System: `Keyboard.current.spaceKey.wasPressedThisFrame`, `Mouse.current.position.ReadValue()`, generated `InputSystem_Actions`, `InputActionReference` | project is new-input-only | Local settings + Official (manual calls Input Manager deprecated); runtime exception behaviour: Check |
| Built-In Render Pipeline shaders/materials | URP shaders; Render Pipeline Converter | Built-In deprecated 6.5 | Official (deprecation); converter workflow: Check |
| `[SerializeField]` on a property | `[field: SerializeField] public T Name { get; private set; }` | compile error since 6.3 | Official |
| Separate TextMeshPro package (`com.unity.textmeshpro`) | merged into uGUI 2.x (`com.unity.ugui`); `using TMPro;` still works | 6.x | Local manifest + changelog |
| Cinemachine 2 (`CinemachineVirtualCamera`, `FreeLook`) | Cinemachine 3 (`CinemachineCamera`, ...), different API | core package in 6.6 | Official; not installed here |
| Muse | Unity AI Assistant | 6.2 | Official |
| Statics reset on every Play | Domain reload disabled by default: reset statics manually | new projects in 6.6 | Official (default) + Local (`m_EnterPlayModeOptions: 1`) |
| `UNITY_64`, `DEVELOPMENT_BUILD` defines | deprecated; see `UNITY_ENABLE_CHECKS` / Managed Code Variant setting | 6.6 | Official |
| Dynamic batching | obsolete | 6.6 | Official |
| `Entities.ForEach`, `IAspect` | removed (DOTS) | 6.5 | Official; not relevant until DOTS |
| Any C# 10+ syntax | C# 9.0 only; Mono / IL2CPP | current | Official |

## Handy URLs
- 6000.6 manual: `https://docs.unity.com/en-us/engine/6000.6/manual` (append `.md` for Markdown)
- Script reference: `https://docs.unity.com/en-us/engine/6000.6/script-reference/unityengine/<class>/<member>`
- API Updater: `.../manual/upgrade-guides/apiupdater`
- Package docs: `https://docs.unity3d.com/Packages/<pkg>@<ver>/manual/`
- Release notes: `https://unity.com/releases/editor/whats-new/6000.6.7`
