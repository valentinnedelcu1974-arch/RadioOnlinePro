# Radio Online Pro — iPhone

Native SwiftUI iOS 17+ player, bundle `com.radioonlinepro.player`, version 1.0.

## Current release candidate

21 VRT stations from the broadcaster's official third-party streaming page. Local search and favorites, direct HTTPS playback, background audio, lock-screen/headset controls, AirPlay, sleep timer, buffering/retry/errors. No public station directory, arbitrary stream entry, ads, analytics SDK, account, purchases or subscriptions. Existing noncatalog favorites are removed during migration. Exact catalog membership is checked before playback.

See [permission register](RIGHTS.md), [privacy](PRIVACY.md) and [support](SUPPORT.md). VRT's publication supports direct listening through smaller apps/services. No VRT logos or endorsement are claimed. Recheck permission before monetization.

## Validation

Build 2 of the previous unrestricted-directory version is available internally in TestFlight; it is NOT the current rights-restricted candidate and must not be submitted in place of this update. The new candidate requires a fresh simulator test, signed upload, Apple processing and physical iPhone checks. See VALIDATION.txt for current evidence. No App Store publication is claimed.

## Build and signing

Extract RadioOnlinePro_iOS_Source.zip, run `xcodegen generate` with Xcode 26.3/XcodeGen, then test the shared RadioOnlinePro scheme. Public build.yml unpacks, runs tests, launches the simulator app and uploads its screenshot/result artifact.

For this account the private Valentinnedelcu repository's radio-testflight.yml workflow reuses existing signing secrets in place. A Radio-specific profile signs `com.radioonlinepro.player`. Credentials are never included in this public package. The standalone public testflight.yml requires separately configured secrets.

## Physical iPhone checks

Play multiple VRT streams; test station switching, pause/resume, reconnect, offline errors, favorites persistence, local search, background/lock-screen playback, headphones, interruptions, AirPlay, sleep timer and accessibility. Station availability and territory restrictions can change.
