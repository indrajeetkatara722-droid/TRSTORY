# Reddit Story Maker - Native Android Application

A complete, high-performance native Android application that turns Reddit stories into viral 9:16 vertical videos (like TikTok, Instagram Reels, and YouTube Shorts) with animated captions, AI narration, procedural Minecraft parkour / endless runner backgrounds, and hardware-accelerated MP4 export.

---

## Architecture & Technology Stack

- **Target OS**: Android 10 (API 29) to Android 16 (API 35)
- **Language**: Kotlin 2.0+
- **UI Framework**: Jetpack Compose & Material 3 (Dark Reddit Theme)
- **Video Pipeline**: Android `MediaCodec` (H.264 surface hardware encoder) + `MediaMuxer`
- **Audio Pipeline**: Android `TextToSpeech` + WebAudio / PCM synthesis
- **Storage**: Storage Access Framework & `MediaStore` (`Movies/RedditStoryMaker`)
- **Background Execution**: `ForegroundService` with Notification Progress to prevent low-RAM (4GB) killed processes
- **Networking**: Retrofit & OkHttp for Gemini 3.8 Flash, OpenAI, and Meta Graph API

---

## How to Open in Android Studio & Build Debug APK

1. **Prerequisites**:
   - Install **Android Studio Ladybug (2024.2+)** or later.
   - Install **JDK 17** or **JDK 21**.

2. **Open the Project**:
   - Launch Android Studio.
   - Click **Open** and select this directory.
   - Wait for Gradle to sync dependencies.

3. **Build Debug APK via Terminal**:
   ```bash
   ./gradlew assembleDebug
   ```
   The generated APK will be located at:
   `app/build/outputs/apk/debug/app-debug.apk`

4. **Install on Phone / Emulator via ADB**:
   ```bash
   adb install -r app/build/outputs/apk/debug/app-debug.apk
   ```

---

## Features Tested & Implemented

| Feature | Android Native Implementation | Web Studio Equivalent |
|---|---|---|
| **AI Story Generator** | Retrofit + Gemini 3.8 Flash + OpenAI | `/api/story/gemini` + `/api/story/openai` |
| **Video Background** | Canvas Hardware Surface + Voxel Renderer | Canvas 2D + 3D Voxel Math + Endless Runner |
| **AI Narration** | Android `TextToSpeech` + AudioRecord | Web SpeechSynthesis + Cloud TTS |
| **8 Caption Styles** | Canvas Text + Dynamic Font Metrics | 8 Templates (White, Karaoke, Single, etc.) |
| **Reddit Card** | Custom Canvas Card + Avatar Clipping | Canvas Vector Snoo + Custom Image |
| **Hardware Export** | `MediaCodec` + `MediaMuxer` (MP4 H.264/AAC) | WebCodecs `VideoEncoder` + `Mp4Muxer` |
| **Gallery Storage** | `MediaStore` (`Movies/RedditStoryMaker`) | Instant Browser Download + Android Sharesheet |
| **Facebook Upload** | Meta Graph API Direct Upload | Secure Express Proxy Upload |
