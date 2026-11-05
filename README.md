# Lock Screen Live Wallpaper

A [Windhawk](https://windhawk.net) mod that plays a video as the background of the Windows 11 **lock screen** and **password / sign-in screen**.

<img src="https://github.com/user-attachments/assets/f8a07449-332b-438b-8992-6dd11cfb554f" width="100%" alt="lslw_preview">

*Preview video: "Stelle Cosmic Cheerleader" by u/iTaiizor, [source](https://www.reddit.com/r/iSucrose/comments/1xirh99/stelle_cosmic_cheerleader/). Character © HoYoverse. The video is not included in this mod.*

## Features

- One video file, or a folder (a random video is picked on every lock)
- Fit modes: cover, fill, fit, center
- Playback speed, color adjustments, optional audio
- Power saving: still-frame mode, pause when idle, boot still frame
- Fail-safe that restores the original wallpaper if something goes wrong

## Requirements

- Windows 11
- [Windhawk](https://windhawk.net)
- `logonui.exe` added to Windhawk's process inclusion list (**Settings → Advanced settings → More advanced settings**)
- A video file the SYSTEM account can read (no network locations, encrypted folders, or cloud-only files)

## Installation

1. Install Windhawk and add `logonui.exe` to the process inclusion list.
2. In Windhawk, click **Create a new mod**.
3. Replace everything in the editor with the contents of [`lock-screen-live-wallpaper.wh.cpp`](lock-screen-live-wallpaper.wh.cpp).
4. Click **Compile Mod**, then set the video path in the mod's **Settings** tab.

Full documentation (settings, performance tips, troubleshooting) is in the mod's readme inside Windhawk.

## Support

- [Ko-fi](https://ko-fi.com/grn15rens)
- [Saweria](https://saweria.co/USERNAME) (for Indonesia)

## License

GPL-3.0, see [LICENSE](LICENSE).

---

## Bahasa Indonesia

Mod [Windhawk](https://windhawk.net) yang memutar video sebagai latar belakang **lock screen** dan **layar password / sign-in** Windows 11.

**Cara pasang:**

1. Pasang Windhawk, lalu tambahkan `logonui.exe` ke daftar inklusi proses (**Settings → Advanced settings → More advanced settings**).
2. Di Windhawk, klik **Create a new mod**.
3. Ganti seluruh isi editor dengan isi file [`lock-screen-live-wallpaper.wh.cpp`](lock-screen-live-wallpaper.wh.cpp).
4. Klik **Compile Mod**, lalu isi path video di tab **Settings** mod.

Dokumentasi lengkap (pengaturan, tips performa, pemecahan masalah) ada di readme mod di dalam Windhawk.
