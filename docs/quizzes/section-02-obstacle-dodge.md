# Section 02 - Obstacle Dodge (lectures 9-35): quiz

**How to use**
1. Take it after finishing the section, video closed, no AI, no notes.
2. Before each answer, write a confidence guess: Low / Medium / High.
3. Answer in your own words (or code) on paper or in a scratch file.
4. Only then open `answers/section-02-obstacle-dodge-answers.md` and check one question at a time.
5. Anything you missed or guessed goes into "Open questions" in `docs/learning-log.md`.

Tags: [Explain] [Predict] [Write] [Which fits?] [Debug] [6.6 trap]

---

1. [Explain] When does `Start()` run, how often does `Update()` run, and why can't you rely on `Update()` running at a fixed rate?
2. [Predict] What does this print on the first three frames? Why?
   ```csharp
   int score;
   void Start() { score = 5; }
   void Update() { score++; Debug.Log(score); }
   ```
3. [Explain] A public field and a `[SerializeField] private` field both show in the Inspector. What is the difference, and which should you prefer?
4. [Write] Write the one line that moves an object along X at 5 units per second using a variable `xValue` (-1 to 1). Why does `Time.deltaTime` matter? What goes wrong at 30 FPS vs 120 FPS without it?
5. [6.6 trap] Lecture 14 uses `Input.GetAxis()`. In **your** project that call fails at runtime. Why? What does Unity tell you, and what would you use instead?
6. [Explain] What is the difference between a collision and a trigger? Name the callback for each and what must be true of the objects for them to fire.
7. [Debug] Two objects with colliders touch, you have `OnCollisionEnter` on one of them, and nothing is logged. Neither has a Rigidbody. What is wrong?
8. [Which fits?] You need the Player's `Rigidbody` every frame. Where do you call `GetComponent<Rigidbody>()`, and what does "caching a reference" mean?
9. [Explain] How do you check that a collided object is tagged "Player"? Why is `CompareTag("Player")` preferred over `tag == "Player"`?
10. [Predict] In which order do `Awake`, `Start`, `OnEnable`, `Update`, `LateUpdate` run? Why would you put "find my own component" in `Awake` and "talk to another object" in `Start`?
11. [Explain] What is a prefab, what is an "override" on a prefab instance, and why did the course turn hazards into prefabs?
12. [Predict] What happens to the object in `Destroy(gameObject, 2f)`? What is different about `Destroy(this)`?
13. [Explain] Name one thing `Time.time` is good for and one thing `Time.deltaTime` is good for.
14. [6.6 trap] Cinemachine is used in lecture 16, but your manifest does not list it. How do you add it, and what changed in Cinemachine 3 compared with the camera component shown in older videos? (Check the docs for the version you install.)

**Rebuild challenge (no video, no AI):** New scene: a player cube moving with WASD that is destroyed (or restarts) when it hits a hazard prefab, with a score that goes up every second. Use the new Input System.
