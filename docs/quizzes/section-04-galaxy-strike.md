# Section 04 - Galaxy Strike (lectures 70-110): quiz

**How to use**
1. Take it after finishing the section, video closed, no AI, no notes.
2. Before each answer, write a confidence guess: Low / Medium / High.
3. Answer in your own words (or code) on paper or in a scratch file.
4. Only then open `answers/section-04-galaxy-strike-answers.md` and check one question at a time.
5. Anything you missed or guessed goes into "Open questions" in `docs/learning-log.md`.

Tags: [Explain] [Predict] [Write] [Which fits?] [Debug] [6.6 trap]

---

1. [Explain] What do a Timeline asset and a `PlayableDirector` do? What is a Signal (emitter / receiver) used for?
2. [Explain] What does an `AnimationCurve` store, and what is one use in a game besides animation?
3. [Write] Clamp a ship's local X between -5 and 5 using `Mathf.Clamp`. Why must you read the value, change it, then write it back?
4. [Predict] What is `Mathf.Lerp(0f, 10f, 0.25f)`? What does `Mathf.Lerp(0, 10, 2)` return, and why?
5. [Explain] You want to rotate the ship smoothly toward a new rotation. Name two `Quaternion` methods for that. Why shouldn't you edit a quaternion's x/y/z/w directly?
6. [Debug] `ps.emission.enabled = true;` does not compile (CS1612). Why, and how do you write it correctly?
7. [Write] Declare an array of `ParticleSystem` lasers and use a `foreach` to turn them all on or off.
8. [Predict] Player at `(1,0,0)`, enemy at `(4,0,4)`. What vector points from the player to the enemy? What is its length? How do you make it length 1?
9. [Explain] What does `Camera.ScreenToWorldPoint` convert? What does the `z` value of the input mean in a perspective camera?
10. [Which fits?] Nested prefab vs prefab variant: when do you want each? Which one did the enemy ship use?
11. [Explain] What is the difference between a Tag and a Layer? Give one use of a layer other than physics.
12. [Which fits?] Another script needs to call `TakeHit()` on the scoreboard. Compare a serialized reference, `FindFirstObjectByType`, and a singleton. Which would you choose and why? Where must a `Find...` call never go?
13. [Explain] What is a coroutine? Write the shape of one that waits 2 seconds and then reloads the level. What happens to it if its GameObject is destroyed or disabled?
14. [6.6 trap] The music singleton uses a `static` instance and `DontDestroyOnLoad`. Write the guard that prevents duplicate music players on level reload. Why can a plain `static` value still behave oddly between Play sessions in your project?
15. [6.6 trap] A post-processing effect is set up but nothing changes in your URP project. Name three things to check (volume, profile, camera).
16. [6.6 trap] Timeline and the scoreboard UI text: where do you find the Timeline window if it's missing, and which namespace do TextMeshPro text components live in now?

**Rebuild challenge (no video, no AI):** A rail-shooter-style ship that moves within clamped bounds, fires lasers (particle system) on input, damages an enemy with hit points, and updates a score text. Use the new Input System.
