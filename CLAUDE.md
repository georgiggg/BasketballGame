# And1 Hoops - CS 4361 Computer Graphics, Team 16

## What we're building
A 3D low-poly 1v1 street basketball game in Unity (C#).
- Outdoor street court at night/dusk, custom skybox, background buildings, streetlights
- Simple shooting mechanics, dribbling, scorekeeping
- Graphics focus (this is a graphics class, so this part matters most for the grade):
  - custom toon/cel shading + outlines
  - particles when a basket is made, trails on shots
  - lighting that sells the street-court atmosphere
- TA feedback we must address: decide and clearly state whether the opponent is AI-controlled or a second player. No networking unless the team explicitly asks for it.

Setup: Unity 6.3 LTS, Universal Render Pipeline (URP), Windows, VS Code, GitHub. Five teammates, all beginners to Unity. Everyone works together using Claude Code, so assume the person talking to you may be any teammate and may not know what was done in earlier sessions.

## How to work with us (most important section)
1. **Ask before each step.** Before starting any milestone or feature, ask me the questions you need answered (preferences, look and feel, controls, scope, anything I've missed). Use multiple-choice where you can and give a recommendation. Don't start building until I answer.
2. **Small steps.** Break each milestone into small pieces that can each be tested in Play mode. Do one piece, then stop.
3. **After each piece, tell me:**
   - what changed (files, GameObjects, components), in a few lines
   - exactly how to test it in Unity (what to click, what keys to press, what I should see)
   - anything I must do by hand in the Editor
   - a short suggested commit message
4. **Changes are normal.** If we change our minds mid-way, adjust the plan and update the notes. Don't fight earlier decisions; just tell us what the change affects.
5. **Don't commit, push, or switch git branches yourself** unless asked. We review and commit ourselves.
6. If something is ambiguous or risky (deleting things, restructuring scenes, adding packages), ask first.
7. Explain things simply when asked. We are new to Unity and need to be able to explain every part of the project in our final demo.

## Your notes (dev-notes/)
Keep your own working notes in `dev-notes/` at the repo root (outside `Assets/`, so Unity ignores it). Keep them short and practical.
- `dev-notes/progress.md` - what's done, what's in progress, what's next. Update after every finished piece.
- `dev-notes/decisions.md` - choices we made and why (controls, opponent type, shader approach, etc.).
- `dev-notes/scene-setup.md` - how the main scene is built (which objects, which scripts, which layers/tags), so a teammate can find their way around.
Read these at the start of every session before doing anything else. Don't put documentation anywhere else and don't write README-style docs inside the code.

## Code style - write like a student on this team would
The code should read like it was written by undergrads learning Unity: clear, simple, a bit plain. Not like a polished framework.
- Plain `MonoBehaviour` scripts. `Start`, `Update`, `FixedUpdate`, `OnTriggerEnter`, simple `if` statements, simple coroutines.
- `[SerializeField] private` fields (or public fields) for values we tune in the Inspector. Sensible defaults.
- One script per job, short files. `PlayerMovement`, `BallController`, `Hoop`, `ScoreManager`, `GameManager`, `CameraFollow` - names a student would pick.
- **No** interfaces, abstract base classes, generics, dependency injection, service locators, event buses, ScriptableObject architectures, or design-pattern scaffolding unless there's a real need and you ask first. A singleton `GameManager` is fine.
- **No** heavy C#: avoid LINQ, tuples, pattern matching, expression-bodied members everywhere, `?.`/`??` chains, `var` everywhere. Normal, readable C#.
- **Comments:** very few. No `///` XML doc comments, no header blocks, no `#region`, no comments that restate the code, no section-divider comments. An occasional short lowercase comment is fine where something isn't obvious (e.g. `// small upward force so the ball doesn't stick to the rim`).
- Don't over-defend: no null checks on every line, no try/catch, no custom exceptions, no input validation layers. Use `Debug.Log` while testing and remove noisy ones when a piece is done.
- Naming: camelCase for fields/locals, PascalCase for methods/classes. Short natural names (`moveSpeed`, `jumpForce`, `ball`, `hoop`, `isGrounded`).
- Keep math readable. If you use a formula (e.g. projectile launch velocity, toon lighting ramp), write it in plain steps with clear variable names so we can explain it.
- Match the style of code that's already in the project. If a teammate wrote something, follow their style.
- No emojis anywhere, in code, logs, or UI text.
- Prefer working with the Unity Editor the way a beginner would: prefabs, Inspector values, tags and layers, Physics Materials, Animator, Particle System, Trail Renderer, Shader Graph or simple HLSL.

## Shaders
For shaders, keep them understandable. Whether we use Shader Graph or hand-written URP HLSL is a team decision - ask. If HLSL, keep it short and readable with only a couple of comments on the lighting math.

## Unity / git rules
- Never edit `.meta` files by hand, never touch `Library/`, `Temp/`, `Logs/`, `UserSettings/`.
- Keep assets organized: `Assets/Scripts`, `Assets/Prefabs`, `Assets/Materials`, `Assets/Shaders`, `Assets/Models`, `Assets/Scenes`, `Assets/Audio`, `Assets/VFX`. Ask before creating new top-level folders.
- Scene files merge badly. Prefer putting work into prefabs. Before large edits to the main scene, remind the user that only one teammate should edit the main scene at a time.
- Third-party assets (free low-poly models, textures, sounds) are allowed only if we agree. Track every one with its source and license in `dev-notes/credits.md`.
- Don't add packages without asking.

## Rough roadmap (flexible - we can reorder, cut, or add)
0. Check the project setup: URP, folders, input system choice, Unity MCP connection working.
1. Graybox court (simple shapes) + player movement + jump + follow camera.
2. Ball: pick up, dribble, shoot with an arc toward the hoop, rim/backboard/ground bounces.
3. Scoring: make detection, 2 vs 3 points by distance, score UI, possession change, win condition.
4. Opponent (AI or second local player - decided with the team).
5. Environment: low-poly court, buildings, streetlights, custom skybox.
6. Graphics: toon shading, outlines, lighting, made-basket particles, shot trails, post-processing if wanted.
7. Player models and animations.
8. Menus, game flow (start, pause, game over), sound.
9. Polish, bug fixing, build, demo prep.

At the start of each milestone, re-read the notes, ask your questions, propose a short plan for that milestone, and wait for approval.