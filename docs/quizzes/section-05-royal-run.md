# Section 05 - Royal Run (lectures 111-148): quiz

**How to use**
1. Take it after finishing the section, video closed, no AI, no notes.
2. Before each answer, write a confidence guess: Low / Medium / High.
3. Answer in your own words (or code) on paper or in a scratch file.
4. Only then open `answers/section-05-royal-run-answers.md` and check one question at a time.
5. Anything you missed or guessed goes into "Open questions" in `docs/learning-log.md`.

Tags: [Explain] [Predict] [Write] [Which fits?] [Debug] [6.6 trap]

---

1. [Which fits?] When do you choose a `for` loop and when a `while` loop? Write a `for` loop that instantiates 5 chunks, each 10 units further along Z.
2. [Explain] `List<T>` vs an array: what can a list do that an array can't? What are `Count` and `Length`?
3. [Predict] A list holds `[A, B, C]`. After `RemoveAt(0)` what does it hold and what is `Count`? Why does removing items inside a `foreach` over the same list throw?
4. [Predict] What is `7 % 3`? Give one game use of the modulus operator.
5. [Write] Lanes are at X = -2, 0, 2. Write an expression that maps the player's X to the nearest lane index 0, 1 or 2.
6. [Explain] What does `Physics Material` friction/bounciness change? What do the "combine" modes decide? What is it called in code in Unity 6? (Look it up.)
7. [Explain] Base class `Pickup` has a method that derived classes change. Explain `virtual` vs `abstract`, and `override`.
8. [Explain] Why use a property such as `public int Score { get; private set; }` instead of a public field?
9. [6.6 trap] You write `[SerializeField] public int Score { get; private set; }` to show it in the Inspector. What happens in Unity 6.6 and what is the correct form?
10. [Explain] "Dependency injection" as used in lecture 134: how does a pickup get a reference to the `ScoreManager` without `Find`? Why is that better?
11. [Explain] `Animator.SetTrigger`, `SetBool`, `SetFloat`: when do you use each? Why use `Animator.StringToHash`?
12. [Predict] You set `Time.timeScale = 0` when time runs out. Which of these stop: movement scaled by `Time.deltaTime`, an animation using unscaled time, `Update()` calls? Why?
13. [Write] Write a countdown timer that never goes below 0, and the check that triggers game over.
14. [Explain] `[Header]` and `[Tooltip]`: what do they do and where do you see the effect?
15. [6.6 trap] Camera shake and Cinemachine: name the two Cinemachine pieces involved in an "impulse" shake (source and listener) and say which package version you must read the docs for.

**Rebuild challenge (no video, no AI):** An endless runner: spawn level chunks with a `for` loop, move them toward the player, destroy and respawn chunks using a `List<T>`, three lanes with clamped player movement, one pickup that adds time or score.
