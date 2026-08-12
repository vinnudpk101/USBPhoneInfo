# USB Phone Info — Advanced Technician Edition 11X

This release upgrades the working Technician Pro project into an automatic USB monitoring build.

## Main upgrades

- Automatic USB bus monitoring while the app is open.
- Automatic connect/disconnect event handling.
- Original connection/disconnection chime assets.
- Automatic model-name resolution from USB descriptors and MTP when available.
- Spoken model announcement after connection.
- No manifest USB attach chooser, so the old "use this app every time" app-selection popup is removed.
- USB permission is requested only when Android has not already granted access.
- VID/PID, USB version, serial when permitted, class/subclass/protocol, configurations, interfaces and endpoints.
- MTP identity lookup.
- ADB interface detection without claiming authorization.
- Fastboot identifier heuristic.
- MediaTek vendor and preloader classification with less overclaiming.
- Qualcomm 9008/EDL identifier classification.
- USB event history.
- Technician report copy/share.
- Read-only diagnostic scope.

## Important Android limitation

Android USB access is a security boundary. `UsbManager.requestPermission()` can display a system permission dialog, and the permission is temporary for that physical USB connection. A normal third-party app cannot silently bypass that control.

The old manifest USB_DEVICE_ATTACHED intent was intentionally removed. That is what caused the Android application chooser/default-app behavior on attachment. The new edition detects devices through live enumeration while the app is open and listens dynamically for disconnect events.

## Build

The included GitHub Actions workflow uses:

- JDK 17
- Gradle 8.7
- Android Gradle Plugin 8.5.2
- compileSdk 35
- targetSdk 35
- Android SDK Platform 35

The workflow expects `USBPhoneInfo_Advanced_11X.zip` in the repository root.
