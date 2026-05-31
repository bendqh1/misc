GZDoom 4.14.2 running TNT: Evilution (no mods)

**Basic data**
- MSI Cubi N ADL-S (Intel Alder Lake-N iGPU)
- Windows 11, updated drivers
- 1080p fullscreen, Vulkan/OpenGL (both rendering APIs tested)
- FPS drops from 60 → ~30–45, especially during effects like berserk/red tint

**Attempts to solve the problem**
- Switching Vulkan ↔ OpenGL (OpenGL slightly better)
- Disabling VSync (removes stutter but causes tearing)
- Lowering sector lights, texture filtering, postprocessing (minimal impact)
- Changing refresh rate (no benefit, sometimes worse)
- FPS monitoring shows classic VSync half-rate drops (60 → 30)
- Windowed mode (almost eliminates issue)
- Render scale reduction (almost eliminates issue)

**Root cause of the problem**
This is not a driver or CPU issue.  
It is a **GPU performance ceiling problem in the Intel Alder Lake-N integrated graphics when running GZDoom’s hardware renderer at 1080p fullscreen**.

When the GPU briefly misses the 60 FPS frame budget, **VSync forces a fallback to ~30 FPS**, causing the visible stutter. The berserk/red screen effect only increases GPU load enough to trigger this, not the underlying problem.

**Best way to cope**
- Use **windowed mode**, or  
- Keep **fullscreen but reduce render scale (~0.8–0.9)**

Both work because they reduce GPU frame time enough to stay consistently above the VSync threshold, preventing the 60 → 30 FPS drop.
