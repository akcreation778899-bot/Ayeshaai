# Ayesha, a voice assistant for Android

Say **"Hey Ayesha"** and she responds. She ignores everything else.

## Build
1. Open this folder in Android Studio (Koala or newer). Let Gradle sync.
2. Run on a real phone (Android 8+). Speech recognition needs a real device.
3. In the app: grant permissions, enable accessibility control, then tap **Start listening**.

## Things to say
- "Hey Ayesha, open YouTube" / "search for weather in Lahore"
- "Hey Ayesha, scroll down" / "go back" / "go home" / "tap Search" / "type hello"
- "Hey Ayesha, play Coke Studio" (opens a media app or YouTube search)
- "Hey Ayesha, set an alarm for 6:30 am"
- "Hey Ayesha, flashlight on" / "volume up" / "volume max" / "mute"
- "Hey Ayesha, turn on Bluetooth" / "Wi-Fi" (asks you to confirm first)
- "Hey Ayesha, send message to Ali saying I'm on my way" (asks to confirm, opens the composer)
- "Hey Ayesha, call Ali" (asks to confirm, opens the dialer)
- "Hey Ayesha, romantic mode" / "friendly mode" / "calm mode"

## Safety design
- **Blocked apps:** `SafetyPolicy.kt` refuses to open or act in banking, payment,
  password-manager, OTP and authenticator apps, matching on package name and app label.
  Add your local banking apps to the lists if they are missed.
- **Accessibility guard:** every scroll, tap and type is refused while a blocked app is
  in the foreground. Password fields are never read or written.
- **Confirmations:** messages, calls, and Wi-Fi/Bluetooth changes always ask "Shall I go ahead?".
  Messages and calls only pre-fill the composer or dialer; you press Send or Call yourself.
- **Memory is opt-in** and off by default.
- **Romantic mode** is clearly fictional roleplay with a light, playful jealousy line only.
  No guilt, pressure, or claims of real feelings.

## Android limits worth knowing
- Android 10+ does not let apps flip Wi-Fi directly, so Ayesha opens the system panel.
- Android 13+ also asks you to approve the Bluetooth prompt.
- "Close app" sends you Home; Android does not let one app kill another.
- Wake word uses the system SpeechRecognizer, which can use more battery and may need
  internet on some phones. For on-device wake word, swap in Picovoice Porcupine with a
  custom "Hey Ayesha" keyword.
- Some phones need Battery > "Unrestricted" for Ayesha so the service is not killed.
