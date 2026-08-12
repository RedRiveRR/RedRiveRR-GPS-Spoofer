# Release Notes

## 1.1.0-rc.10

Public prerelease for Intel and Apple Silicon Macs. This is not a stable release.

- Session Mode is the only location simulation mode. Persistent Mode has been removed, along with its recovery state, so a withdrawn feature can no longer raise a restore warning.
- Adds Turkish and English localization with an in-app language switch under **Settings -> General**. The choice is remembered across launches.
- Adds device hot-plug handling: connecting an iPhone after launch, and disconnect followed by reconnect, are detected without restarting the app.
- Retry now performs a real rediscovery instead of reusing cached runtime and device handles.
- Restore no longer stalls: the helper IPC write is bounded, and device polling pauses while a session owns the iPhone.
- Production licensing is active. Keys are delivered by email, revealed on the claim page and activated in the app.
- Physically tested on Intel and Apple Silicon Macs: Apply, Stop, Restore, repeated Apply/Stop/Restore cycles, and hot-plug reconnect.
- 244 deterministic macOS tests pass with 0 failures. Universal `arm64`/`x86_64`, deployment target macOS 12.7.
- Remains unsigned and unnotarized by design. iOS 17.0-17.3.x remains unsupported.

Only the DMG and SHA-256 file are published as Release assets. Source code remains private.

## 1.1.0-rc.9 - Developer Mode Test

Public test prerelease for Intel and Apple Silicon Macs. This is not a stable release.

- Adds selected-device Developer Mode status reporting and a **Prepare Developer Mode** action for unlocked, trusted USB iPhones.
- Uses Apple's device service to reveal the Developer Mode setting without Xcode, 3uTools, root, `sudo`, administrator AppleScript, or a kernel/userspace tunnel.
- Keeps Apple's required user steps explicit: enable Developer Mode on the iPhone, restart, confirm after reboot, and refresh status in the app.
- Blocks a new Apply when a modern selected device explicitly reports Developer Mode disabled without consuming a free use.
- Leaves Clear, Stop, and safety cleanup unchanged and available in every runtime, counter, and license state.
- Preserves the existing app-managed `pymobiledevice3==10.3.0` runtime and the same separately supplied evaluation test-key flow.
- Passes 122 deterministic macOS tests with 0 failures and ships as build 115 for universal `arm64`/`x86_64` Macs.
- RC8's existing product paths were physically validated on two M4 Macs and one 2018 Intel Mac; RC9's first-use preparation still needs external testing on an iPhone where Developer Mode has never been revealed.
- Remains unsigned and unnotarized; iOS 17.0-17.3.x remains unsupported.

Only the DMG and SHA-256 file are published as Release assets. Source code remains private.

## 1.1.0-rc.8

Release candidate for Intel and Apple Silicon Macs.

- Fixes the conflicting state where a valid manual Python runtime enabled Apply but persistent userspace DVT later rejected it.
- Keeps manual Python available for device discovery while requiring the verified app-managed runtime for persistent Apply sessions.
- Keeps the generated Terminal setup command visible when a healthy manual runtime is detected.
- Prevents a runtime setup failure from being mislabeled as **Unsupported iOS**; newer reported iOS 26.x versions remain on the userspace DVT strategy.
- Preserves the five locally persisted free successful single-point changes and separately supplied RC8 test-key flow.
- Documents that the separately supplied evaluation test receipt expires no later than 12 August 2026 at 23:31 UTC; production licensing remains inactive.
- Keeps Clear, Stop, and safety cleanup available regardless of runtime, counter, or license state.
- Passes 115 deterministic macOS tests with 0 failures and ships as a universal `arm64`/`x86_64` build.
- Remains unsigned and unnotarized; iOS 17.0-17.3.x remains unsupported, and broader physical-device UI validation is still ongoing.

This is not a stable release. License keys are distributed separately and are not included in the repository or Release notes.

## 1.1.0-rc.7

Release candidate for Intel and Apple Silicon Macs.

- Adds five locally persisted free successful single-point location changes for a fresh app profile.
- Locks new location changes at `0/5` until a separately supplied valid RC7 license key is activated.
- Failed Apply operations do not consume a free use; verified licensed use does not consume the local counter.
- Keeps Clear, Stop, and safety cleanup available in every counter and license state.
- Uses a guided, copyable Terminal command for the app-managed `pymobiledevice3==10.3.0` runtime, followed by explicit **Check Runtime** health verification.
- Retains direct app-owned userspace DVT location sessions on iOS 17.4 and later without root, `sudo`, administrator AppleScript, or a persistent kernel tunnel.
- Includes the monochrome app branding and corrected DMG presentation for Intel and Apple Silicon.
- Passes 114 deterministic macOS tests with 0 failures.
- Remains unsigned and unnotarized; iOS 17.0-17.3.x remains unsupported, and broader physical-device UI validation is still ongoing.

This is not a stable release. License keys are distributed separately and are not included in the repository or Release notes.

## 1.1.0-rc.3

Release candidate for Intel and Apple Silicon Macs.

- Refined monochrome branding and installer presentation.
- Improved explicit device selection and location-session lifecycle behavior.
- Uses direct userspace location support on iOS 17.4 and later without root or a persistent kernel tunnel.
- Includes managed-runtime compatibility improvements for macOS.
- Stop sends Clear and closes the app-owned session; physical GPS restoration must still be confirmed on the device.
- iOS 17.0-17.3.x remains unsupported.
- Full physical UI validation and final signed/notarized distribution remain pending.

This is not a stable release.
