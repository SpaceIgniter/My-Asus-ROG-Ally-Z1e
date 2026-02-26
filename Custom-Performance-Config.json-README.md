# Ryujinx Custom Performance Config for ROG Ally Z1 Extreme

**Device Compatibility**: ROG Ally Z1 Extreme only. This config leverages RDNA3-specific features and may not work optimally on other handhelds.

## Installation Instructions

Ryujinx Config.json file - location = Open Ryujinx > Click on the File Menu Option > Choose Open Ryujinx Folder (*Backup original Ryujinx Config.json file first*) > Paste downloaded Config.json file in same directory, replace current Config.json  

The File is a highly optimised AI-assisted Config file that is tweaked for a ROG Ally Z1e specifically. Insane performance results. tested in highly demanding titles.

## Expected Performance Improvements

- **Eliminated shader compilation stutters** during gameplay
- **Smooth frame pacing** on the 120Hz display
- **Reduced input latency** via VRR (Variable Refresh Rate)
- **Console-like plug-and-play experience** with no desktop UI
- **Sharper visuals** with FSR upscaling
- **Consistent performance** in demanding titles like Tears of the Kingdom

## Asus ROG Ally Z1 Extreme Optimised Config.json: The Changes

| Setting                         | Change                      | Reasoning                                                                                                                                                   |
|---------------------------------|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| graphics_backend_multithreading | OFF → ON                    | The Shader Fix: Offloads shader compilation to the Z1E's extra CPU threads. This eliminates the "Stop-and-Build" stutters.                                  |
| tick_scalar                     | 100 → 50                    | The Timing Fix: Aligns the emulator's internal clock with the Ally's high-refresh hardware. Resolves micro-jitters/frame-pacing issues.                     |
| enable_vsync & vsync_mode       | ON → OFF (0)                | The VRR Fix: Disabling VSync while using a 120Hz interval allows the ROG Ally's Variable Refresh Rate to handle frame delivery for zero-latency smoothness. |
| custom_vsync_interval           | 60 → 120                    | The Cap Fix: Sets the "ceiling" for the VRR window, ensuring the game stays within the Ally's optimal sync range.                                           |
| memory_manager_mode             | Software → HostMappedUnsafe | The Speed Fix: Bypasses software checks to allow the GPU to access memory at native speeds. Essential for consistent 30-60FPS in TotK.                      |
| docked_mode                     | False → True                | The Visual Fix: Forces the game to use 1080p internal assets, making it look sharp on monitors while the Ally's Z1E easily handles the load.                |
| scaling_filter                  | Bilinear → FSR              | The Clarity Fix: Uses AMD's FidelityFX Super Resolution to keep the image crisp even when undocked.                                                         |
| start_no_ui & fullscreen        | OFF → ON                    | The Handheld Fix: Launches the game as a console experience; no mouse or keyboard required to start playing.                                                |

## ⚠️ Important Note on HostMappedUnsafe

The **memory_manager_mode** setting is set to "HostMappedUnsafe" for maximum performance, but this may cause crashes or stability issues in some games. If you experience instability:

1. Open Ryujinx
2. Go to Options > Settings > System
3. Change Memory Manager Mode to **"HostMapped"** (safer, still fast) or **"SoftwarePageTable"** (most compatible)

## Philosophy

This configuration transitions Ryujinx from a generic 'Desktop PC' emulator into a console-like experience specifically tuned for the ROG Ally's RDNA3 GPU and 120Hz VRR display. It prioritises background shader building and frame-pacing stability over standard compatibility defaults.
