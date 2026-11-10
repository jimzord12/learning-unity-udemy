---
name: lesson-checkpoint
description: Scaffolds a new course section or lesson folder, runs a pre-commit hygiene check for Unity (.meta pairs, ignored directories, Force Text, LFS), drafts a commit message, and creates the annotated section started/finished git tags. Use when the user says "commit", "checkpoint", "end of lesson", "set up the next section", "start section N", "finished section N" or "tag".
disable-model-invocation: true
---

# Lesson checkpoint

Manual-only and **read-only**: this skill inspects and advises. It never creates folders, stages, commits, tags or pushes by itself. It gives the learner the exact commands to run; it runs one only if the learner explicitly asks for that specific action.

## A. Set up the next section / lesson
Ask for the section number and topic. Suggest this layout; the learner creates it in the Editor/Explorer:
```
Assets/Course/SectionNN_Topic/
  Scripts/  Prefabs/  Materials/  Scenes/
```
Scene per lesson: `Scenes/L03_PlayerMovement.unity`. Creating `.unity`/`.prefab` files must be done in the Editor (never hand-written): tell the learner what to click. Folders created outside the Editor lack `.meta` until Unity next focuses; remind them to let the Editor import before committing.

## B. Hygiene check before a commit
Run and summarise (read-only):
1. `git status --short` and `git diff --stat`.
2. Every new/changed file under `Assets/` has a matching `.meta` (and no `.meta` is orphaned from a deleted asset).
3. Nothing from `Library/`, `Temp/`, `Logs/`, `UserSettings/`, `*.csproj`, `*.slnx` is staged.
4. `ProjectSettings/EditorSettings.asset` still has `m_SerializationMode: 2` (Force Text); Visible Meta Files still on.
5. Large binaries (png/jpg/fbx/wav/mp3/psd...) are covered by `git lfs` rules in `.gitattributes` (`git lfs ls-files` after staging).
6. No unintended mass YAML diffs (Unity 6.6 disabled YAML word-wrap, so a first reserialize can be noisy: mention, don't "fix").
7. `research_notes/` and `reports/` are git-ignored by the learner's decision; make sure they are not staged.

## C. Draft the commit
- One commit per lesson. Message: `section_NN lesson_L: <what was built>`; body: one line on what the learner understood or is still unsure of (from `docs/learning-log.md`).
- Show the suggested message and the file list; the learner runs `git add` / `git commit` themselves. Never run them, and never push, unless explicitly asked.
- Include the commit trailer required by the session's attribution instructions, if any.

## D. Section tags (when a section, or several, is started or finished)
Convention: an **annotated** tag at the start and at the end of a section (or batch). Zero-pad section numbers to two digits.
1. Ask: started or finished? Which section(s)?
2. Confirm `git status` is clean and `HEAD` is the commit to tag (run section B and C first if not).
3. Check the tag name is free: `git tag -l "section*-05*"` etc. Never overwrite, move or delete an existing tag without asking.
4. Show the command for the learner to run (run it yourself only if they explicitly ask):
   - `git tag -a section-05-started -m "Started Section 05"`
   - `git tag -a section-05-finished -m "Finished Section 05"`
   - `git tag -a sections-05-to-10-started -m "Started Sections 05 to 10"`
   - `git tag -a sections-05-to-10-finished -m "Finished Sections 05 to 10"`
5. Verify with `git show section-05-started --no-patch`. Do not push tags unless asked.

Before a "finished" tag, offer the `lecture-coach` weekly blank-scene rebuild and a learning-log entry for the section.
