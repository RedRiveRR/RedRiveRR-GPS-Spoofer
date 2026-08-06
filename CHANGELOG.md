# Release Notes

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
