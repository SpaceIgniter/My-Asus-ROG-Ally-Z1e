# Ryujinx Custom Performance Config for ROG Ally Z1 Extreme
**Device Compatibility:** ROG Ally Z1 Extreme only. This config leverages RDNA3-specific features and high-refresh VRR logic.
## 🛠 Prerequisites
* **VRAM Setting:** Set your ROG Ally VRAM to **6GB** (or "Auto") in Armoury Crate/BIOS. *The default 4GB will cause stutters even with this config.*
* **Drivers:** Ensure you are on the latest Asus/AMD GPU drivers.
## 📥 Installation Instructions
1. Open Ryujinx.
2. Click **File** > **Open Ryujinx Folder**.
3. **Backup** your original `Config.json` (rename it to `Config.json.bak`).
4. Paste the downloaded `Config.json` into this directory, replacing the current file.
5. Restart Ryujinx.
## 🚀 Expected Improvements
* **Eliminated Shader Stutter:** Smooth gameplay even when entering new areas.
* **Perfect Frame Pacing:** Optimised for the Ally's 120Hz display.
* **Low Latency:** Uses VRR (Variable Refresh Rate) for a "snappy" controller feel.
* **Console Experience:** Launches straight into the game, fullscreen, with no desktop UI.
## 🔍 The Changes: Stock vs. Optimised
| Setting | Change | Reasoning |
| :--- | :--- | :--- |
| **graphics_backend_multithreading** | OFF → ON | **The Shader Fix:** Offloads compilation to extra CPU threads. |
| **tick_scalar** | 100 → 50 | **The Timing Fix:** Aligns emulator clock with 120Hz hardware to stop micro-jitters. |
| **enable_vsync & vsync_mode** | ON → OFF (0) | **The VRR Fix:** Allows the Ally's VRR to handle frame delivery for zero-latency. |
| **custom_vsync_interval** | 60 → 120 | **The Cap Fix:** Sets the ceiling for the VRR window. |
| **memory_manager_mode** | Software → HostMappedUnsafe | **The Speed Fix:** Bypasses software checks for native GPU memory speeds. |
| **docked_mode** | False → True | **The Visual Fix:** High-quality 1080p internal assets for a crisp image. |
| **scaling_filter** | Bilinear → FSR | **The Clarity Fix:** AMD FidelityFX Super Resolution for sharp handheld play. |
| **start_no_ui & fullscreen** | OFF → ON | **The Handheld Fix:** True console-like, plug-and-play experience. |

> ⚠️ **Note on Stability:** `HostMappedUnsafe` is used for maximum performance. If a specific game crashes, change **Memory Manager Mode** to `HostMapped` in **Options > Settings > System**.  

## Philosophy
This configuration transitions Ryujinx from a generic 'Desktop PC' emulator into a console-like experience specifically tuned for the ROG Ally's RDNA3 GPU. It prioritises background shader building and frame-pacing stability over standard compatibility defaults.
