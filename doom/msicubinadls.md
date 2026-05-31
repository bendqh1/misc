**Summary:**  
GZDoom 4.14.2 running TNT: Evilution on an MSI Cubi N ADL-S under **Windows 11 Home** shows lag only in certain map areas. The issue is unlikely to be caused by CPU performance, Windows 11 Home, thermal throttling, dynamic lights, brightmaps, or VSync. Vulkan performs better than OpenGL on this system.

**Most likely cause:** An interaction between GZDoom's Vulkan renderer and the Intel UHD graphics driver.

**Advice:** Update to the latest Intel graphics driver directly from Intel, disable texture filtering and anisotropic filtering in GZDoom, and try borderless fullscreen. If the issue remains, it is likely a GZDoom rendering issue specific to the Intel integrated graphics rather than a general hardware performance problem.
