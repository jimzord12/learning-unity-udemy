# Section 01 - Introduction & Setup (lectures 1-8): quiz

**How to use**
1. Take it after finishing the section, video closed, no AI, no notes.
2. Before each answer, write a confidence guess: Low / Medium / High.
3. Answer in your own words (or code) on paper or in a scratch file.
4. Only then open `answers/section-01-introduction-and-setup-answers.md` and check one question at a time.
5. Anything you missed or guessed goes into "Open questions" in `docs/learning-log.md`.

Tags: [Explain] [Predict] [Write] [Which fits?] [6.6 trap]

---

1. [Explain] What is the difference between the Unity Hub and the Unity Editor? Which one decides which Editor version a project opens in?
2. [Explain] Your project folder has `Assets/`, `Library/`, `Packages/`, `ProjectSettings/`, `Logs/`, `Temp/` and `UserSettings/`. In one line each: what is it for, and which of these should never be committed to git?
3. [Explain] What is a GameObject? What is a Component? Which Component does every GameObject always have?
4. [Explain] Name the six main Editor windows from lecture 5 (Scene, Game, Hierarchy, Inspector, Project, Console) and say what each is for. What is the difference between the Scene view and the Game view?
5. [Predict] Next to `TestDeleteMe.cs` there is a `TestDeleteMe.cs.meta`. You close Unity and rename `TestDeleteMe.cs` to `Foo.cs` in File Explorer. What happens when you reopen Unity, and why does it matter for anything that referenced that script?
6. [Which fits?] You want to rename or move an asset. Where should you do it, and why?
7. [Explain] How does VS Code know which Unity project/editor to talk to? Where in Unity do you choose the external script editor?
8. [Explain] Lecture 4 was a Unity security update. Where would you check which patch version of your Editor line is the latest, and how do you read your project's current version without opening the Editor?
9. [6.6 trap] When you open your project, the Console shows `Unable to use UDP port ... for VS/Unity messaging`. Is that an error in your code? Which package prints it, and does it block you from learning?
10. [6.6 trap] The course was recorded on an early Unity 6 build. You are on 6000.6.7f1. Name two official places you would check first when something in the video does not match your Editor.

**Rebuild challenge (no video, no AI):** Create a new empty scene, add a cube and a plane, move the cube above the plane, and press Play. Then say what each Inspector section of the cube (Transform, Mesh Filter, Mesh Renderer, Box Collider) does.
