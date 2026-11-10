# Section 06 answers (check only after you attempted each question)

1. A NavMesh is a baked map of walkable surface. A `NavMeshAgent` plans a path on it and moves the object. Stopping distance = how close to the target before stopping; radius/height = agent size for clearance; step/jump height = how big a ledge it can climb/drop.
2. The **AI Navigation** package (`com.unity.ai.navigation`) provides `NavMeshSurface`. Your manifest does not list it, so check Window > Package Manager (Unity Registry) and install it if the lecture's baking workflow isn't available. Check the package docs for the version shown.
3. `agent.SetDestination(player.position);` (call it in `Update` at a sensible rate, or when the target moves). Stop with `agent.ResetPath()` / `isStopped`.
4.
   ```csharp
   if (Physics.Raycast(cam.position, cam.forward, out RaycastHit hit, 100f))
   {
       Debug.Log(hit.collider.name);
   }
   ```
5. `layerMask` limits which layers the ray can hit (e.g. ignore the player's own collider or triggers); `QueryTriggerInteraction` decides whether trigger colliders count. Using a mask avoids hitting yourself and is faster.
6. A data container asset that lives in the project, not in a scene. Use: weapon stats (damage, fire rate, ammo). `[CreateAssetMenu(fileName = "Weapon", menuName = "Weapons/Weapon")]`.
7. ScriptableObjects are assets; edits in the Editor are written to the asset and persist. In a built game, changes live only in memory for that session. So don't treat them as per-run state unless you copy them or reset on start.
8. `if (Time.time >= lastShotTime + cooldown) { Shoot(); lastShotTime = Time.time; }`
9. `10`. `fov = zoomed ? 20f : 60f;`
10. Toggling `SetActive` on children is simple and fast; instantiating on switch saves scene objects but costs allocation and needs cleanup (pooling later if needed). Use the simple version first.
11. Hitscan: instant, easy to aim, no travel time; projectiles: travel time and can be dodged, but need physics/lifetime handling and cost more. Sniper = hitscan (per the course), turret = projectile.
12. `Collider[]`. Loop through them: `foreach (var c in hits) { if (c.TryGetComponent(out EnemyHealth h)) h.TakeDamage(dmg); }`. `OnDrawGizmos` draws the radius in the Scene view so you can tune it. Gizmos are Editor-only and do not run in a build.
13. `OnEnable() { Publisher.OnEvent += Handler; }` and `OnDisable() { Publisher.OnEvent -= Handler; }`. Forgetting `-=` leaves a dead subscriber that is still called (errors, duplicate calls, memory leaks).
14. With **domain reload off**, the static event (and its subscriber list) survives between Play sessions, so handlers from destroyed objects remain. Fix: always unsubscribe in `OnDisable`/`OnDestroy`, and/or clear the event in a `[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.SubsystemRegistration)]` method (`OnEnemyDied = null;`), or avoid a static event.
15. `rb.linearVelocity = transform.forward * speed;`
16. Counter plus event is best: each enemy notifies when it dies, and a manager decrements the counter. `FindObjectsByType` every frame is wasteful (and was a version-specific API); a plain counter alone requires every spawn/death to touch it correctly, the event keeps it decoupled.

**Rebuild challenge hints:** AI Navigation package + baked surface, `SetDestination`, `Physics.Raycast` with `out RaycastHit`, `[CreateAssetMenu]` ScriptableObject, `Time.time` cooldown, an event on enemy death with matching unsubscribe.
