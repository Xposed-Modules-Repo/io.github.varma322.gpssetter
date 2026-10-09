# GPS Setter

An Xposed module that sets your device's location, built on the modern
[libxposed](https://github.com/libxposed/api) API for LSPosed 2.x / Vector.

Fork of [jqssun/android-gps-setter](https://github.com/jqssun/android-gps-setter),
which builds on [Android1500/GpsSetter](https://github.com/Android1500/GpsSetter).

## Features

- System-wide spoofing on Android 12+: every location fix (GPS, network, fused)
  is replaced inside the system server, so apps don't need to be scoped one by one.
- Continuous 1 Hz fix generation, so Google Play services apps follow the set
  location with Google Location Accuracy left on — even indoors with no GPS signal.
- Real location during emergencies: while an emergency call/SMS is active
  (Android 14+), real fixes pass through untouched.
- Start, stop and location changes apply immediately, without a reboot.
- On-screen joystick to nudge the location live.
- Random-position jitter around the set point.

## Requirements

- Rooted device with **LSPosed 2.x or Vector** (libxposed API 101+).
  LSPosed 1.x cannot load this module.
- Android 8.1+. System-wide spoofing of live updates needs Android 12+.

## Setup

1. Enable **GPS Setter** in LSPosed and tick **System Framework** in its scope
   (optionally also tick individual apps).
2. Reboot.
3. Open the app, pick a location on the map and press play.

## Notes

- Apps protected by Google Play's anti-tamper (those bundling `libpairipcore.so`)
  crash if scoped — don't scope them; rely on the system hook.
- Only enable one location-spoofing module at a time.

Source code & issues: https://github.com/varma322/android-gps-setter
