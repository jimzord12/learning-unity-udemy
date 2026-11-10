# Section 06 - Sharp Shooter (lectures 149-191): quiz

**How to use**
1. Take it after finishing the section, video closed, no AI, no notes.
2. Before each answer, write a confidence guess: Low / Medium / High.
3. Answer in your own words (or code) on paper or in a scratch file.
4. Only then open `answers/section-06-sharp-shooter-answers.md` and check one question at a time.
5. Anything you missed or guessed goes into "Open questions" in `docs/learning-log.md`.

Tags: [Explain] [Predict] [Write] [Which fits?] [Debug] [6.6 trap]

---

1. [Explain] What is a NavMesh and what does a `NavMeshAgent` do with it? What are "stopping distance", "agent radius" and "step/jump height" for?
2. [6.6 trap] In Unity 6 which package provides the `NavMeshSurface` component used to bake a NavMesh? Is it in your manifest? How would you find out / add it?
3. [Write] Sketch a method that makes an enemy chase the player using a `NavMeshAgent`. Which call sets the target position?
4. [Write] `Physics.Raycast` returns a bool and fills a `RaycastHit`. Write the call that fires from the camera forward up to 100 units and logs the name of what it hit.
5. [Explain] What do the `layerMask` and `QueryTriggerInteraction` overloads change? Give one reason to use a layer mask when shooting.
6. [Explain] What is a ScriptableObject? Name a good use for one in a shooter, and what attribute lets you create it from the Assets menu?
7. [Debug] You change a value on a ScriptableObject asset *while the game is playing in the Editor* and the new value is still there after you stop. Why? Is that true in a built game?
8. [Write] Implement a shooting cooldown using `Time.time` (store when you last shot). Write the condition.
9. [Predict] What is `int x = (5 > 3) ? 10 : 20;`? Rewrite `if (zoomed) { fov = 20; } else { fov = 60; }` as a ternary.
10. [Which fits?] Weapon switching: compare keeping all weapons as children and toggling `SetActive`, versus instantiating the weapon when you switch. Which is simpler for this project and what is the cost of the other?
11. [Explain] Hitscan (raycast) weapons vs projectile weapons: one gameplay and one technical trade-off. Which does the sniper use and which does the turret?
12. [Predict] `Physics.OverlapSphere(position, 5f)` returns what type? How would you apply damage to every enemy in the explosion? Why does `OnDrawGizmos` help here, and does it ship in a build?
13. [Explain] In the event system lecture, how do you subscribe and unsubscribe to a C# `event Action` and in which two methods? What bug appears if you forget to unsubscribe?
14. [6.6 trap] You declare `public static event Action OnEnemyDied;` and subscribe from a MonoBehaviour in `OnEnable`. After several Play/Stop cycles you get `MissingReferenceException` from old subscribers. Why in your project, and what are two fixes?
15. [6.6 trap] A projectile script sets `rb.velocity = transform.forward * speed;`. What should it be in Unity 6?
16. [Which fits?] Counting remaining enemies for the win condition: compare calling `FindObjectsByType` every frame, keeping a counter, and an event when each enemy dies. Which is best and why?

**Rebuild challenge (no video, no AI):** First-person scene with a NavMesh enemy that chases you, one hitscan gun with a cooldown and ammo defined by a ScriptableObject, enemy health, and a win message when all enemies are dead.
