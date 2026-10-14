# Test report - v1.0.1

## Real-phone result for v1.0.0 (reported by the owner)
- Video recorded fine (82 s). The AAC audio track was silent (mean volume -91 dB). He was recording a live Zoom lecture in the Zoom app. Zoom call audio is VoIP, which Android playback capture generally cannot capture, so this is the likely cause (not confirmed on device).

## Passed for v1.0.1 (build machine only)
- Debug APK built with Java 17, Gradle 8.2, Android SDK 34 (versionCode 2, versionName 1.0.1). Manifest checked with aapt2: RECORD_AUDIO, FOREGROUND_SERVICE_MEDIA_PROJECTION, FOREGROUND_SERVICE_MICROPHONE present.
- Ten standalone Java checks of CaptureMath (scaling, clipping-safe mixing and adding, timing).

## NOT verified (no Android device or emulator available to the builder)
- The audio fix has not run on any phone. It is a code change based on reading the source and Android's documented behavior, not a confirmed fix. The Zoom/VoIP cause is a strong hypothesis, not confirmed. The mic backup in Zoom is also unverified: Zoom holds the mic itself and some phones will not share it.
- Live meter, mic fallback switching, mixing sync and notification text were not runtime-tested. Lint was not re-run for 1.0.1.
- Hour-long recording, rotation, vendor battery limits: unchanged and unverified.

## Required phone check
1. Uninstall v1.0.0 if the install fails, then install v1.0.1.
2. Keep the default Auto mode, start a recording, play the lecture for 10-15 seconds and watch the Internal bar.
3. Stop, open the file in a player and confirm sound. Note which player app and option you used and whether the bar moved or the status said MIC BACKUP.
4. If the file is silent and the Internal bar never moved, the player blocks capture; use Auto with the speaker on, or the player's own permitted download.
