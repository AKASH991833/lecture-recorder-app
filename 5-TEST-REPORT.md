# Test report - v1.0.0

## Passed
- Android debug APK build with Java 17, Gradle 8.2, Android SDK 34.
- Android lint: zero errors. Remaining warnings concern hardcoded Hinglish labels and conservative free-space checks.
- Eight standalone Java assertions: portrait/landscape scaling, clipping-safe audio mixing, one-second timing, five-hour timing without overflow, and invalid dimensions.
- Source inspection: screen permission per session, Android 14 projection foreground service, optional microphone foreground type, scoped Movies storage, Stop action, stop on projection withdrawal, encoder EOS, resource cleanup, failure deletion of incomplete pending file, bounded startup queue.

## Not verified
- A real Android phone is not available for this build.
- Android emulator could not boot: host lacks sufficient RAM and hardware acceleration. Both Android 14 and Android 10 images reported insufficient RAM, so there is no claim of runtime capture or audio validation.
- Internal audio from any specific LMS, mic/system mixing synchronization, screen-rotation behavior on older devices, phone-vendor battery restrictions, and hour-long recordings remain unverified.
- Public screenshots are clearly labeled UI previews if no emulator screenshot is available. They are not evidence of a real-phone recording.

## Required first phone check
1. Install APK on Android 10 or newer.
2. Select Internal audio, start recording and accept Android's screen prompt.
3. Play a permitted 10-second lecture clip, stop via notification.
4. Open Gallery > Movies > LectureRecorder. Check readable video and audible sound.
5. Repeat for Internal + mic if needed. Wear headphones to avoid doubled speaker audio.
6. Rotate once during a short test; video uses the starting canvas and can become letterboxed. Start in landscape for a landscape lecture.
7. Do not rely on this for a full class until those checks pass. If the player blocks video/audio, use its permitted recording/download option. No bypass is provided.
