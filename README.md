<div align="center">

# Lock Screen Live Wallpaper

**Play a video or animated GIF as the background of the Windows 11 lock screen and sign-in screen.**

[![Version](https://img.shields.io/badge/version-1.1.0-blue?style=for-the-badge)](https://github.com/grn15RenS/lock-screen-live-wallpaper/releases/latest)
[![Windhawk](https://img.shields.io/badge/Windhawk-mod-8A2BE2?style=for-the-badge)](https://windhawk.net/mods/lock-screen-live-wallpaper)
[![Windows 11](https://img.shields.io/badge/Windows-11-0078D4?style=for-the-badge&logo=windows11&logoColor=white)](#requirements)
[![License](https://img.shields.io/badge/license-GPL--3.0-green?style=for-the-badge)](LICENSE)

[**Install from Windhawk**](https://windhawk.net/mods/lock-screen-live-wallpaper) ·
[**Releases**](https://github.com/grn15RenS/lock-screen-live-wallpaper/releases) ·
[**Report a bug**](https://github.com/grn15RenS/lock-screen-live-wallpaper/issues)

<br>

<img src="https://i.imgur.com/QFNE1hY.gif" alt="Lock Screen Live Wallpaper preview" width="800">

<sub>Preview video: "初音未来——抖音翩翩" (Hatsune Miku) by 古月方源, <a href="https://steamcommunity.com/sharedfiles/filedetails/?id=3802463919">source</a>. Character © Crypton Future Media, INC. The video is not included in this mod.</sub>

</div>

---

## Overview

A [Windhawk](https://windhawk.net) mod that runs inside `LogonUI.exe`, decodes your video or animated GIF, and feeds the frames into the XAML image elements Windows normally uses for the lock screen wallpaper. If anything looks wrong, a built-in fail-safe restores the original wallpaper.

## Highlights

| | |
| --- | --- |
| 🎬 **Video and GIF** | `mp4`, `m4v`, `mov`, `wmv`, `avi`, `mkv` and animated `gif`, as a single file or a folder |
| 🖼️ **Fit modes** | Cover, fill, fit (letterbox) and center |
| 🔊 **Audio** | Optional audio track with smooth fade in and fade out |
| 🎨 **Color and look** | Hue, saturation, brightness, contrast, gamma and dim |
| ⚡ **Hardware decoding** | GPU decoding (D3D11/DXVA) with automatic software fallback |
| 🔋 **Power saving** | Still-frame mode, pause when idle, and a low battery saver |
| 👀 **Preview window** | Check fit, colors and speed without locking your PC |
| 🛡️ **Fail-safe** | Restores the original wallpaper if the UI changes or the mod misbehaves |

## What's new in 1.1.0

- **Preview window**: opens from the settings, a hotkey or a tray icon, and can draw the real clock, date and status icons over the video.
- **Animated GIF support**, alone or inside a folder.
- **Low battery saver** with light, balanced and maximum modes.
- **Dim** setting, **folder order** (random, sequential, fixed) and **audio fade**.
- **Configurable still frame duration** right after boot.
- **Cache housekeeping** and faster color processing.
- **Fixes**: padded frame heights (for example 1088 for 1080) are cropped correctly, audio restarts with the video on every loop, and quick unlocks no longer trip the crash guard.

See the full changelog in the mod's readme inside Windhawk.

<div align="center">

<img src="https://i.imgur.com/KFW2K91.gif" alt="Preview window" width="640">

<sub>The preview window playing the video, with the clock, date and status icons drawn over it.</sub>

</div>

## Requirements

- Windows 11
- [Windhawk](https://windhawk.net)
- `LogonUI.exe` added to Windhawk's process inclusion list (see below)
- A video file the **SYSTEM** account can read. `LogonUI.exe` runs as SYSTEM, so network locations, encrypted folders and cloud-only files may not work. A normal local folder is the safest choice.

## Installation

1. Install [Windhawk](https://windhawk.net).
2. Open Windhawk and go to **Explore**.
3. Search for [Lock Screen Live Wallpaper](https://windhawk.net/mods/lock-screen-live-wallpaper).
4. Open the mod page and click **Install**.
5. Add `LogonUI.exe` to the process inclusion list (next section).
6. In the mod settings, set **Video file or folder** to your video.

### Add LogonUI.exe to the inclusion list

`LogonUI.exe` is a protected system process, so Windhawk does not inject into it by default.

1. Open Windhawk and go to **Settings** → **Advanced settings** → **More advanced settings**.
2. Add `LogonUI.exe` to the **Process inclusion list** and save.

<div align="center">
<img src="https://i.imgur.com/9Biip4G.png" alt="Windhawk advanced settings: process inclusion list" width="560">
</div>

## Settings at a glance

| Group | What you can change |
| --- | --- |
| **General** | Video file or folder, folder order, fit mode, audio volume, video speed (25% to 400%) |
| **Color adjustments** | Hue, saturation, brightness, contrast, gamma, dim |
| **Performance** | Render width (320 to 1920) and hardware video decoding |
| **Pause and power saving** | Still frame, pause when idle, low battery saver |
| **Screens and startup** | Play on the password screen, shutdown screen, behavior right after boot |
| **Preview** | Preview window, hotkey, tray icon, stay on top, clock/date/status overlay |
| **Debug log** | Optional `debug.log` with CPU and decode statistics |

Detailed notes for every setting are in the mod's readme inside Windhawk.

## Performance tips

- Lower **Render width** (try 1280 or 960). It is the biggest CPU lever.
- Keep **Hardware video decoding** on for 4K or 60 fps videos. Without it, prefer 1080p at 30 fps.
- Keep **Pause when idle** enabled so nothing is decoded while nobody is at the PC.
- Use the low battery saver on laptops.
- If the video stutters while you type your password, turn off **Play video on the password screen**.

## Fail-safe

The mod stops itself and restores the original wallpaper for the rest of that `LogonUI.exe` process when:

- the video decoder fails before producing any frame,
- no video frame is produced within 30 seconds,
- the lock screen elements are never found (usually a Windows update changed the UI), or
- the UI throws repeated errors.

A separate crash guard turns playback off if two sign-in sessions in a row end before the first frame is shown. Changing the video, render width, fit mode or hardware decoding turns it back on.

## Troubleshooting

| Problem | Try this |
| --- | --- |
| Normal wallpaper is shown | Make sure `LogonUI.exe` is in the process inclusion list and the video path is correct, then turn on **Debug log** and read `debug.log` |
| Video will not open | Use an H.264 MP4 stored somewhere the SYSTEM account can read |
| No sound | Set **Audio volume** above 0 |
| Stuttering | Lower the render width and check the `CPU` and `UI stalls` lines in the log |
| Preview hotkey does nothing | Write it like `Ctrl+Alt+P` and check that no other program already uses it |

The log folder (regular Windhawk install):

```
C:\ProgramData\Windhawk\Engine\ModsWritable\mod-storage\lock-screen-live-wallpaper
```

`ProgramData` is hidden, so paste the path into the File Explorer address bar.

## Report a bug

Please [open an issue](https://github.com/grn15RenS/lock-screen-live-wallpaper/issues) and include:

- your Windows 11 version (for example 25H2)
- `debug.log` (turn on **Debug log** first)
- Windhawk's log (enable logging for the mod in Windhawk)

The logs contain the video path, so remove anything personal first if you prefer.

## Support

If you enjoy this mod, you can support its development:

- [Ko-fi](https://ko-fi.com/grn15rens)
- [Saweria](https://saweria.co/grn15RenS) (for Indonesia)

## License

This mod is licensed under the GPL-3.0. See [LICENSE](LICENSE) for details.

## Disclaimer

Only tested on Windows 11 23H2 and 25H2. This mod runs inside a system UI process (`LogonUI.exe`), so it includes a fail-safe that restores the original wallpaper if anything goes wrong. As a precaution, keep another way to sign in available while trying it out.
