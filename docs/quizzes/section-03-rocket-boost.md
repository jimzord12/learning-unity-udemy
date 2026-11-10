# Section 03 - Rocket Boost (lectures 36-69): quiz

**How to use**
1. Take it after finishing the section, video closed, no AI, no notes.
2. Before each answer, write a confidence guess: Low / Medium / High.
3. Answer in your own words (or code) on paper or in a scratch file.
4. Only then open `answers/section-03-rocket-boost-answers.md` and check one question at a time.
5. Anything you missed or guessed goes into "Open questions" in `docs/learning-log.md`.

Tags: [Explain] [Predict] [Write] [Which fits?] [Debug] [6.6 trap]

---

1. [Which fits?] `AddForce` vs `AddRelativeForce`: what is the difference, and which one makes a rocket thrust along its own nose direction?
2. [Explain] When you rotate a Rigidbody yourself (not via physics), why might you temporarily stop physics from rotating it too? What property is involved?
3. [Explain] Describe the structure of an Input Actions asset: Action Map -> Action -> Binding. How does your script read a float value from an Action, and what must be done to the action before it reports anything?
4. [Explain] What is a namespace for? What does `using UnityEngine;` do? Why must a MonoBehaviour class name match its file name?
5. [Write] Rewrite this as a `switch` on the tag, including the default:
   ```csharp
   if (tag == "Friendly") { Debug.Log("ok"); }
   else if (tag == "Finish") { LoadNext(); }
   else { Crash(); }
   ```
6. [Explain] You call `SceneManager.LoadScene(1)` and nothing loads. What do you check first? What's the Unity 6 name for the window where scenes are listed?
7. [Write] How do you load "the next scene, or back to the first scene after the last"? Sketch the logic using `buildIndex` and `sceneCountInBuildSettings`.
8. [Explain] What does `Invoke("ReloadLevel", 1f)` do? Give one downside of using a method name in a string, and one alternative.
9. [Explain] `AudioSource`, `AudioClip`, `AudioListener`: what does each do? Why is `PlayOneShot` often better than `Play` for sound effects?
10. [Debug] A thrust sound restarts every frame while the key is held and sounds like a stutter. What check do you add before playing?
11. [Explain] Why add a bool such as `isTransitioning` when the rocket crashes or reaches the landing pad?
12. [Predict] An object's Y is set to `Mathf.Sin(Time.time)` times 2. Between which values does it move and roughly how long is one full cycle? How would you make it a 4-second cycle?
13. [6.6 trap] A script has `static int deaths;` that increments on each crash. You press Stop, then Play again. Why might `deaths` *not* be 0 on the second run in your project? Name two ways to fix it.
14. [6.6 trap] The course's Rigidbody tuning lecture mentions `drag` and `angularDrag`. In your Editor what are they called now, in the Inspector and in code?

**Rebuild challenge (no video, no AI):** A rocket cube with W for thrust and A/D for rotation, a sound and a particle effect while thrusting, a landing pad that loads the next scene, and a crash that reloads after a short delay. Use the new Input System.
