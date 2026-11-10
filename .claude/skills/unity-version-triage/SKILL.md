---
name: unity-version-triage
description: Diagnoses why older Udemy/tutorial Unity code fails in Unity 6.6 (6000.6) and maps removed or changed APIs to their replacements. Use on compile errors, obsolete or "does not exist" warnings, pink materials, InvalidOperationException about UnityEngine.Input, static state behaving oddly between Play sessions, or "the course code doesn't work".
---

# Unity version triage (Unity 6000.6)

Version drift is the commonest reason course code breaks. Diagnose it before treating it as the learner's bug, but keep the learner doing the reasoning.

## Procedure
1. **Read the message.** Ask the learner to paste the exact Console text (you cannot see the Editor). Or read `Logs/Editor.log` and search for `error CS`.
2. **Learner hypothesis first:** "What do you think this error means? Which line?"
3. **Match against** `references/breaking-changes.md` (table of old -> new).
4. **Check the docs** for the exact symbol: `https://docs.unity.com/en-us/engine/6000.6/script-reference/unityengine/<class>/<member>.md`. Check the `version` front matter.
5. **Scan upgrade guides** newest first: `https://docs.unity.com/en-us/engine/6000.6/manual/upgrade-guides/upgrade-guide-unity66.md`, then `unity65`, `unity64`, ... down to `upgrade-guide-unity6`.
6. Only then ask which lecture this is from. The course ("Complete C# Unity 3D Game Development in Unity 6") was recorded on a Unity 6 beta (6000.0 line), so also check the 6.0 upgrade guide (`upgrade-guide-unity6`) and whether the lecture used a beta-only API, package version or template. If the Editor UI differs from the video, ask for a screenshot.
7. Give hint-ladder rungs, not a full rewrite, unless the learner says "show me". Explain *why* the API changed.

## Symptom shortcuts
- Runtime exception mentioning the legacy Input / `UnityEngine.Input` -> project is new-Input-System only. Teach `Keyboard.current` / generated `InputSystem_Actions`. Temporary workaround: Player Settings > Active Input Handling > Both.
- Static counters, singletons or events keep values after pressing Stop/Play -> domain reload is off. Reset in `[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.SubsystemRegistration)]`, unsubscribe in `OnDisable`, or re-enable domain reload (Project Settings > Editor > Enter Play Mode Settings).
- Pink / magenta materials -> Built-In shaders in a URP project. Use the Render Pipeline Converter or switch the material to a URP shader.
- "'X' does not contain a definition for 'rigidbody'/'camera'/..." -> 6.5 removed the shortcuts; use `GetComponent<T>()`.
- Code using `FindObjectOfType` or `Rigidbody.velocity/drag` -> use the new names (see table).
- C# syntax errors on modern syntax (file-scoped namespace, `record struct`, `required`, raw strings) -> Unity compiles C# 9.

## Don'ts
- Don't upgrade the Editor or packages to "fix" a course. 6.6 is non-LTS and the learner is mid-course.
- Don't hand-edit scene/prefab/ProjectSettings YAML; tell the learner what to click.
