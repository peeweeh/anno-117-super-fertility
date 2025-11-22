## Core Principles
- Keep everything simple: Short code/docs first—add complexity only for mod features (e.g., farm tweaks). Why: Faster in-game testing.
- Follow DRY: Reuse XML snippets across mods; remove obvious fluff (e.g., no redundant imports). Why: Anno mods load quicker.
- Use standard naming: e.g., `balance-plan.md`, `production-plan.md` in /plans. Limit folders: /data for mod files, /references for reference docs. Why: Matches repo structure and mod.io upload format.
- Confidence threshold: Always mention confidence per task (e.g., "98% on production tweak"). If <99%, ask for clarification. Why: Avoids game crashes from unverified mods.
- Wait for user to validate in game and proceed only after confirmation. Why: Ensures mod works before further steps.

## Planning and Updates
- Base everything on /plans files: Use as primary input (e.g., /plans/farm-balance.md). Create/update plans for all tasks in /plans folder. Why: Centralizes mod ideas without extra files.
- Handle ad-hoc changes: Integrate into /plans seamlessly; commit often, push at end. Update README/plan.md post-validation only. Why: Keeps repo clean for iterative fun.

## Execution Guidelines
- Code/Mod practices: Short comments with *why* (e.g., "// Double production for better balance"). Readable XML for community fixes. Simple first (tweak existing before new). Why: Anno modders share easily.
- Tools: Focus on local (e.g., text editor for XML); if external, self-run and fix. Skip AWS unless specified. Why: Pure modding stays lightweight.
- Docs: Light with TL;DRs. For README/docs, use emojis (🌾 for farms, ⚡ for production), bold headers, bullets for nice reading. Explain *why* in comments/docs (e.g., "This mod increases fertility because..."). Update README/plan.md only after in-game validation—no rewrites without testing. Why: Makes mod.io descriptions engaging and clear.

## Workflow Check
- Always verify: Tasks in /plans done? In-game validated? Confidence >99%? README/plan.md updated? Mod.io-ready? Why: Delivers stable, shareable Anno 117 mods.
