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

This release candidate may be unsigned and unnotarized. It is provided for evaluation while final Apple distribution credentials and physical UI validation are completed.

## Runtime Setup

The current DMG does not bundle a standalone Python runtime. On a clean Mac without compatible Python 3, install Python 3 first, reopen the app, and use its managed-runtime setup or repair flow. The app-managed environment pins `pymobiledevice3==10.3.0` and does not require administrator privileges.

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
