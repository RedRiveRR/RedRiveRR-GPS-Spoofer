<p align="center">
  <img src="assets/redrivrr-logo.png" alt="RedRiveRR GPS Spoofer" width="144">
</p>

<h1 align="center">RedRiveRR GPS Spoofer</h1>

<p align="center">
  <a href="https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/tag/v1.1.0-rc.10"><img alt="Release" src="https://img.shields.io/badge/release-v1.1.0--rc.10-black?style=for-the-badge"></a>
  <img alt="License" src="https://img.shields.io/badge/license-proprietary-black?style=for-the-badge">
  <img alt="macOS" src="https://img.shields.io/badge/macOS-12.7%2B-black?style=for-the-badge&logo=apple">
  <img alt="Architectures" src="https://img.shields.io/badge/Universal-Intel%20%2B%20Apple%20Silicon-black?style=for-the-badge">
  <img alt="Tests" src="https://img.shields.io/badge/tests-122%20passing-brightgreen?style=for-the-badge">
</p>

> RedRiveRR GPS Spoofer is proprietary, closed-source software. This repository is the official binary distribution page and does not provide source code or permission to copy, modify, reverse engineer, or redistribute the software except as expressly stated in the license.

[Türkçe](README.tr.md) · [Release notes](CHANGELOG.md) · [Security](SECURITY.md) · [License](LICENSE)

## Current Release

Version `1.1.0-rc.10` is a public test prerelease. It is not a stable release.

Session Mode is the only location simulation mode; Persistent Mode has been removed. This release adds Turkish and English localization with an in-app language switch, device hot-plug detection and reconnect handling, and runtime repair support.

This build is unsigned and not notarized. That is intentional — see the installation steps below.

The universal binary contains both `x86_64` and `arm64` slices, and this release has been physically tested on Intel and Apple Silicon Macs.

- [Download the universal DMG](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/download/v1.1.0-rc.10/RedRiveRR-GPS-Spoofer-1.1.0-rc.10-universal.dmg)
- [Download the SHA-256 checksum](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/download/v1.1.0-rc.10/RedRiveRR-GPS-Spoofer-1.1.0-rc.10-universal.dmg.sha256)

Published SHA-256:

```text
517262bb6b77d02bd26c1f0f04666772c15222feb6451eaae9df59a3554e25a6
```

## Requirements

| Component | Requirement |
| --- | --- |
| macOS | 12.7 or later |
| Mac | Intel or Apple Silicon |
| iPhone | iOS 16+ requires Developer Mode; the app can prepare the setting for the selected trusted USB device |
| Connection | Unlocked, trusted USB connection recommended |
| iOS | Userspace support for iOS 17.4 and later; iOS 17.0-17.3.x is unsupported |
| Runtime | Compatible Python 3 is required when no healthy app-managed runtime exists |

No jailbreak, root access, `sudo`, administrator AppleScript, or persistent kernel tunnel is required.

## Install

1. Download the DMG and checksum from the release page.
2. Verify the checksum in Terminal:

   ```bash
   shasum -a 256 RedRiveRR-GPS-Spoofer-1.1.0-rc.10-universal.dmg
   ```

3. Open the DMG and drag **RedRiveRR GPS Spoofer** to **Applications**.
4. Launch the app, connect and trust the iPhone, then select the target device explicitly.

RC10 is unsigned and unnotarized. This is intentional and permanent for this product; there is no Apple Developer ID signature and no notarization ticket. Follow the Gatekeeper steps below on first launch.

## Developer Mode

The app provides a **Prepare Developer Mode** action for the explicitly selected, unlocked, trusted USB iPhone. It asks Apple's device service to reveal the Developer Mode setting without Xcode, 3uTools, root, `sudo`, administrator AppleScript, or a tunnel.

Apple still requires the user-controlled completion steps. After preparation succeeds, open **Settings → Privacy & Security → Developer Mode** on the iPhone, enable it, accept the restart, and confirm **Enable** after reboot with the device passcode. Return to the app and refresh the status before applying a location.

The existing location, runtime, license, Clear, Stop, and safety-cleanup paths were regression tested. The new first-use preparation flow still requires external validation on an iPhone where Developer Mode has never previously been revealed or enabled.

## macOS Gatekeeper Warning

RC10 is not signed with an Apple-issued Developer ID certificate and has not been notarized by Apple. The current DMG therefore produces the warning that macOS cannot verify the developer or check the app for malicious software. This warning means Gatekeeper has no usable signature or notarization ticket for the app; it does not mean macOS completed a malware check and approved the app.

Only continue if you downloaded the DMG from the official RedRiveRR GitHub Release and its SHA-256 matches the value published above.

To open the current RC using Apple's supported security-exception flow:

1. In the warning dialog, choose **Cancel** or **Done**. Do not move the app to the Bin.
2. On macOS Ventura 13 or later, open **System Settings → Privacy & Security**. On macOS Monterey 12, open **System Preferences → Security & Privacy → General** and unlock the preference pane if requested.
3. Select **Open Anyway** for RedRiveRR GPS Spoofer.
4. Authenticate with your Mac login password or Touch ID when requested.
5. When the warning appears again, select **Open**.

Apple states that **Open Anyway** is available for about one hour after the blocked launch attempt. If it is not visible, try to launch the app once more and return to Privacy & Security. A Mac managed by a company or school may prevent this override.

Do not disable Gatekeeper and do not use Terminal commands to remove quarantine. These broad workarounds weaken macOS protection and are not part of the supported installation process. See Apple's [Open apps safely on your Mac](https://support.apple.com/en-gb/102445) guidance.

The permanent publisher-side fix requires Apple Developer Program access and a new build signed with an Apple **Developer ID Application** certificate using Hardened Runtime and a secure timestamp, submitted to Apple's notary service, and distributed with the notarization ticket stapled to the DMG. The release must then pass `codesign`, `stapler`, and Gatekeeper assessment before publication. Apple explains this distribution model in [Developer ID certificates](https://developer.apple.com/help/account/certificates/create-developer-id-certificates) and [resolving notarization issues](https://developer.apple.com/documentation/security/resolving-common-notarization-issues). A correctly signed and notarized replacement build should open through the normal macOS confirmation flow without this unidentified-developer warning.

## Runtime Setup

The app uses a guided Terminal setup instead of attempting a silent installation inside the app. It does not install Python itself. A healthy manual Python runtime is sufficient for device discovery, but persistent userspace location sessions require the verified app-managed runtime.

When a compatible Python 3 exists, the command displayed by **Runtime Setup**:

- creates an isolated virtual environment at `~/Library/Application Support/RedRiveRR GPS Spoofer/Runtime/venv`;
- installs `pymobiledevice3==10.3.0`, `urllib3<2`, `cryptography<47`, and their dependencies inside that environment;
- applies the macOS socket-buffer compatibility patch and prepares the bundled location-session helper for verification;
- does not use root, `sudo`, administrator privileges, Homebrew changes, global pip installation, or user-site package changes.

### First Runtime Installation

1. Keep the Mac connected to the internet and launch the app.
2. Open **Runtime Setup** beside **Need help?**. If it reports that Python is missing, install Python 3 from the official Python website, reopen the app, and return to Runtime Setup.
   If it reports **Manual Python runtime**, the app may discover devices but Apply remains unavailable. The app keeps the required Terminal command visible so you can complete the app-managed setup.
3. Copy the complete command shown by the app and select **Open Terminal**.
4. Paste the command into Terminal, press Return, and wait for the completion message. Package download and setup can take several minutes.
5. Return to the app and select **Check Runtime**. Continue only after it reports a healthy app-managed runtime with `pymobiledevice3 10.3.0` and the correct host architecture.
6. Connect, unlock, and trust the iPhone, refresh the device list, and select the target device explicitly.

Use the exact generated command rather than a global `pip install`. Do not add `sudo`. The app accepts the managed runtime only after package, architecture, userspace DVT CLI, patch metadata, socket preflight, and helper health checks pass.

### Mac With No Python

The current DMG does not bundle a standalone Python runtime. On a genuinely clean Mac with no compatible Python 3, install Python 3 first, reopen Runtime Setup, and run the command displayed by the app. This remains a release-candidate limitation; a future truly self-contained DMG requires a signed bundled Python runtime or compiled native helper.

### Clean Reinstall Test

To test the managed installer again without modifying system tools:

1. Stop any active location session and quit RedRiveRR GPS Spoofer normally.
2. Move only `~/Library/Application Support/RedRiveRR GPS Spoofer/Runtime` to the Bin.
3. Do not remove `/usr/bin/python3`, Xcode Python, Homebrew Python, the whole RedRiveRR Application Support directory, Keychain items, history, or favorites.
4. Reopen the app and follow **First Runtime Installation** above. The app will not reinstall dependencies until you run the displayed Terminal command.

Removing the Runtime directory deletes the app-managed Python packages. It does not uninstall the app or delete saved history and favorites.

## Free Uses And License Key

- A fresh local app profile starts with `5/5` free successful single-point location changes.
- Each successful **Apply Location**, favorite, or history coordinate update consumes one free use. A failed Apply does not consume a use.
- The remaining count is stored locally and persists when the app is closed or the Mac restarts.
- At `0/5`, new location changes are locked until a valid license key is activated.
- Route and joystick functions are not unlocked by the free-use counter.
- Clear, Stop, and safety cleanup are never blocked by the counter or license state.

License keys are not published in this repository or in Release notes. Do not post a key in GitHub Issues, screenshots, or logs.

Production licensing is active in this release. A purchased key is delivered by email, revealed on the claim page, and activated in the app under **License**. Activation is verified against a signed receipt; the raw key is never stored after verification.

## Use And Safety

- Apply starts a userspace location session for the explicitly selected device.
- Coordinate updates use the app-owned session while it is running.
- Stop sends the Clear command and shuts down the owned session.
- Clear, Stop, and safety cleanup remain available regardless of license state.
- A completed Clear command does not independently prove the iPhone's physical GPS state. Confirm restoration in Apple Maps or Compass.

## Network And Privacy

- Location commands are sent locally to the selected device.
- Apple MapKit may download map data.
- Runtime setup may download pinned packages and dependencies.
- Update checks may request public GitHub release metadata.
- Production payment and online licensing are active. Activation and periodic licence refresh contact the RedRiveRR licensing service.

## Support

Use [GitHub Issues](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/issues) for reproducible product problems without including license keys, device identifiers, personal location data, logs containing secrets, or other private information. Report security issues using the private process in [SECURITY.md](SECURITY.md).

## License

Copyright © 2024-2026 RedRiveRR. All rights reserved. This software is proprietary and closed source. See [LICENSE](LICENSE).
