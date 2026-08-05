<p align="center">
  <img src="assets/redrivrr-logo.png" alt="RedRiveRR GPS Spoofer" width="144">
</p>

<h1 align="center">RedRiveRR GPS Spoofer</h1>

<p align="center">
  <a href="https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/tag/v1.1.0-rc.3"><img alt="Release" src="https://img.shields.io/badge/release-v1.1.0--rc.3-black?style=for-the-badge"></a>
  <img alt="License" src="https://img.shields.io/badge/license-proprietary-black?style=for-the-badge">
  <img alt="macOS" src="https://img.shields.io/badge/macOS-12.7%2B-black?style=for-the-badge&logo=apple">
  <img alt="Architectures" src="https://img.shields.io/badge/Universal-Intel%20%2B%20Apple%20Silicon-black?style=for-the-badge">
</p>

> RedRiveRR GPS Spoofer is proprietary, closed-source software. This repository is the official binary distribution page and does not provide source code or permission to copy, modify, reverse engineer, or redistribute the software except as expressly stated in the license.

[Türkçe](README.tr.md) · [Release notes](CHANGELOG.md) · [Security](SECURITY.md) · [License](LICENSE)

## Current Release

Version `1.1.0-rc.3` is a prerelease release candidate for Intel and Apple Silicon Macs. It is not a stable release.

- [Download the universal DMG](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/download/v1.1.0-rc.3/RedRiveRR-GPS-Spoofer-1.1.0-rc.3-universal.dmg)
- [Download the SHA-256 checksum](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/download/v1.1.0-rc.3/RedRiveRR-GPS-Spoofer-1.1.0-rc.3-universal.dmg.sha256)

Published SHA-256:

```text
146f0edb94a482e62d953fd9982f5d6f2a0b98c6ce7a9b35fabee1f84be38ffa
```

## Requirements

| Component | Requirement |
| --- | --- |
| macOS | 12.7 or later |
| Mac | Intel or Apple Silicon |
| iPhone | Developer Mode enabled |
| Connection | Unlocked, trusted USB connection recommended |
| iOS | Userspace support for iOS 17.4 and later; iOS 17.0-17.3.x is unsupported |
| Runtime | Compatible Python 3 is required when no healthy app-managed runtime exists |

No jailbreak, root access, `sudo`, administrator AppleScript, or persistent kernel tunnel is required.

## Install

1. Download the DMG and checksum from the release page.
2. Verify the checksum in Terminal:

   ```bash
   shasum -a 256 RedRiveRR-GPS-Spoofer-1.1.0-rc.3-universal.dmg
   ```

3. Open the DMG and drag **RedRiveRR GPS Spoofer** to **Applications**.
4. Launch the app, connect and trust the iPhone, then select the target device explicitly.

RC3 is unsigned and unnotarized. It is provided for evaluation while final Apple distribution credentials and physical UI validation are completed.

## macOS Gatekeeper Warning

RC3 is not signed with an Apple-issued Developer ID certificate and has not been notarized by Apple. The current DMG therefore produces the warning that macOS cannot verify the developer or check the app for malicious software. This warning means Gatekeeper has no usable signature or notarization ticket for the app; it does not mean macOS completed a malware check and approved the app.

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

The app installs its own `pymobiledevice3` environment, but it does not install Python itself.

If a compatible Python 3 already exists, the app can:

- create an isolated virtual environment at `~/Library/Application Support/RedRiveRR GPS Spoofer/Runtime/venv`;
- install `pymobiledevice3==10.3.0`, `urllib3<2`, `cryptography<47`, and their dependencies inside that environment;
- apply and verify the macOS socket-buffer compatibility patch and verify the bundled location-session helper;
- complete the setup without root, `sudo`, administrator privileges, Homebrew changes, global pip installation, or user-site package changes.

This behavior was validated on an Intel Mac using compatible Xcode Python 3.9.6. Starting without an app-managed runtime produced a fresh environment, installed the pinned package, applied the 7 MiB socket-buffer fallback, and reached `ready` in approximately 2 minutes 16 seconds. Installation time depends on the Mac and network/cache state.

### First Runtime Installation

1. Keep the Mac connected to the internet and launch the app.
2. Leave the app open while **Environment Setup** checks Python and creates the managed runtime. This can take several minutes.
3. If installation does not start or the status remains unhealthy, select **Install Managed Runtime**. Use **Repair Runtime** for a partial or incompatible installation.
4. Wait for the status to show `ready`, `pymobiledevice3 10.3.0`, the host architecture, and successful userspace DVT/socket-buffer checks.
5. Connect the iPhone only after runtime setup is ready, then refresh and select the device explicitly.

Do not manually run `pip install pymobiledevice3`, do not install it globally, and do not use `sudo`. A separate older user installation can be incompatible even though the app-managed runtime works.

### Mac With No Python

The current DMG does not bundle a standalone Python runtime. On a genuinely clean Mac with no compatible Python 3, automatic dependency installation cannot start. Install a compatible Python 3 distribution first, reopen the app, select **Check Again**, then allow the app to create its managed runtime. This remains a release-candidate limitation; a future truly self-contained DMG requires a signed bundled Python runtime or compiled native helper.

### Clean Reinstall Test

To test the managed installer again without modifying system tools:

1. Stop any active location session and quit RedRiveRR GPS Spoofer normally.
2. Move only `~/Library/Application Support/RedRiveRR GPS Spoofer/Runtime` to the Bin.
3. Do not remove `/usr/bin/python3`, Xcode Python, Homebrew Python, the whole RedRiveRR Application Support directory, Keychain items, history, or favorites.
4. Reopen the app and follow **First Runtime Installation** above.

Removing the Runtime directory deletes the app-managed Python packages. It does not uninstall the app or delete saved history and favorites.

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
- Production payment and licensing are not active in this release candidate.

## Support

Use [GitHub Issues](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/issues) for reproducible product problems without including license keys, device identifiers, personal location data, logs containing secrets, or other private information. Report security issues using the private process in [SECURITY.md](SECURITY.md).

## License

Copyright © 2024-2026 RedRiveRR. All rights reserved. This software is proprietary and closed source. See [LICENSE](LICENSE).
