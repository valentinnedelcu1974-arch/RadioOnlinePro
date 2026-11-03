# Radio Online Pro — iPhone

Native SwiftUI app, iOS 17+, bundle ID `com.radioonlinepro.player`, version 1.0.

Implemented: Romanian/world station discovery via Radio Browser; HTTPS personal streams; local saved stations and favorites; search; background playback; lock-screen and headset controls; AirPlay; 15/30/60/90-minute sleep timer; buffering, connection timeout and failed-stream messages; handling audio interruptions and unplugged headphones; app icon; privacy manifest and in-app privacy information. No advertising, purchases, subscriptions or user account.

## Actual validation status

Source, YAML/JSON/plist and workflow shell syntax passed validation. Xcode 26.3 simulator tests passed (2 tests), the app launched successfully and loaded the Romanian station directory. The real simulator screenshot is included in Preview/RadioOnlinePro-Simulator.png.

The corrected signed archive and IPA export succeeded; App Store Connect accepted version 1.0 build 2 with no upload errors. Apple processing and internal TestFlight availability are checked separately. App Store publication has not occurred. Real iPhone audio, background/lock-screen playback and AirPlay still require device testing. App Review contacts/release choices await the owner's specific approval after an automatic approval-review block. No purchases or subscriptions have been enabled.

The first upload was rejected because an XcodeGen default included iPad; the app target now explicitly limits TARGETED_DEVICE_FAMILY to iPhone. The upload script now treats Apple's UPLOAD FAILED text as a failure even if altool returns zero.


## Build

Download and extract RadioOnlinePro_iOS_Source.zip. Inside RadioOnlinePro, install Xcode 26.3 and XcodeGen. Run `xcodegen generate`; open RadioOnlinePro.xcodeproj. The shared RadioOnlinePro scheme includes URL validation and station identity tests. `.github/workflows/build.yml` builds/tests on an iPhone simulator, launches the app and saves a validation artifact. A launch smoke test does not validate actual audio or every interaction.

## Same Apple account as Grid Management Pro

Use the existing Apple Developer/App Store Connect account. Radio Online Pro requires its own bundle registration, App Store Connect app record and matching App Store distribution profile. The Grid Management Pro provisioning profile cannot sign this bundle ID. Do not modify or revoke Grid's working assets.

The distribution certificate and App Store Connect API key may be reused where their permissions allow, but GitHub secrets cannot be read or copied from another repository. They must be configured securely in this repository by the owner/authorized session or made available through an appropriately authorized secret scope. Never commit credentials.

TestFlight workflow configuration:

- Variable `APPLE_TEAM_ID`: actual existing Apple Team ID.
- Variable `RADIO_PROFILE_NAME`: name of the new profile for this Radio bundle.
- Secret `RADIO_APPSTORE_PROFILE_BASE64`: the Radio-specific distribution profile.
- Same secret names as Grid for reusable assets: `IOS_DISTRIBUTION_P12_BASE64`, `IOS_DISTRIBUTION_P12_PASSWORD`, `ASC_KEY_ID`, `ASC_ISSUER_ID`, `ASC_PRIVATE_KEY_BASE64`.

The existing private Valentinnedelcu repository also contains a separate manual radio-testflight.yml workflow. It downloads the public Radio source and uses the existing signing secrets in place, plus a new Radio-specific provisioning profile; credentials remain private. Apple Team ID F3639777XM, bundle registration com.radioonlinepro.player and App Store Connect app 6830363430 have been verified. The RadioOnlinePro_AppStore profile was generated using the existing distribution certificate.

For this existing Apple account, use the private radio-testflight.yml workflow to reuse credentials in place. The public standalone testflight.yml requires its own configured secrets. Run the simulator workflow first. Resolve failures. Then run TestFlight manually. Verify both successful upload and Apple processing before inviting an internal tester. No payments are activated by these workflows.

## Physical iPhone acceptance tests

1. Discover Romanian stations; search a different name; change to world stations; verify loading and empty/error messages.
2. Play at least three available streams; switch stations while buffering; pause/resume; reconnect after disabling/restoring internet.
3. Favorite posts, relaunch, confirm persistence; delete from a filtered saved list and confirm the correct station is removed.
4. Add an HTTPS audio stream; reject HTTP, blank names and credential-bearing URLs; ensure duplicates are not added.
5. Lock iPhone; confirm audio and lock-screen controls; test Bluetooth/headphones and unplug behavior; test incoming phone call and permitted resumption.
6. Test AirPlay with a compatible receiver. Set a 15-minute sleep timer, cancel/change it, and verify playback pauses at expiration.
7. Check VoiceOver, large text and small iPhone layouts. Capture actual screenshots and a review demo only from a verified build.

## Directory and privacy

Radio Browser is an external community directory: https://www.radio-browser.info and https://docs.radio-browser.info/. Streams connect directly to broadcasters. Only HTTPS entries are shown. Availability, content and territorial restrictions depend on broadcasters; directory inclusion does not grant distribution rights. Confirm intended station/content rights before App Store submission.

Favorites and personal station lists use device-local UserDefaults. Search terms go to Radio Browser, and directory/stream servers receive the user's IP and connection details. No tracking or analytics SDK is included. The local privacy manifest does not by itself determine the App Store privacy answers; evaluate external service practices before publishing those answers.

Support contact: valentin.nedelcu@icloud.com. A public support/privacy URL, actual screenshots, age rating, content-rights answers and App Review details still require completion. Store listing copy is supplied in APP_STORE_DRAFT.txt.
