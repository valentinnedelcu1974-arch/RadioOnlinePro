# Radio Online Pro — iPhone

Native SwiftUI iOS 17+ player, bundle `com.radioonlinepro.player`, version 1.0.

## Current release candidate

21 VRT stations from the broadcaster's official third-party streaming page. Local search and favorites, direct HTTPS playback, background audio, lock-screen/headset controls, AirPlay, sleep timer, buffering/retry/errors. No public station directory, arbitrary stream entry, ads, analytics SDK, account, purchases or subscriptions. Existing noncatalog favorites are removed during migration. Exact catalog membership is checked before playback.

See [permission register](RIGHTS.md), [privacy](PRIVACY.md) and [support](SUPPORT.md). VRT's publication supports direct listening through smaller apps/services. No VRT logos or endorsement are claimed. Recheck permission before monetization.

## Validation

The rights-restricted candidate passed Xcode simulator tests and launched successfully. Its real screenshot is in Preview/RadioOnlinePro-Simulator.png. Signed archive/export and App Store Connect upload succeeded for version 1.0 build 3. Build 2 contains the old unrestricted directory and must not be submitted instead. See VALIDATION.txt for evidence and limits. Physical iPhone playback has not been verified. App Store publication has not occurred.

## App Store preparation

Public support/privacy pages, VRT-only listing text and current screenshot have been entered. Free pricing, distribution territories, age rating and privacy labels remain to be finalized. Automated review blocked the worldwide content-rights attestation because the broadcaster's stream publication alone does not establish that broad warranty; see RIGHTS.md for the actual evidence. Free pricing and automatic public release also require explicit owner authorization. No legal warranty or App Store submission is claimed.

## Build and signing

Extract RadioOnlinePro_iOS_Source.zip, run `xcodegen generate` with Xcode 26.3/XcodeGen, then test the shared RadioOnlinePro scheme. Public build.yml unpacks, runs tests, launches the simulator app and uploads its screenshot/result artifact.

For this account the private Valentinnedelcu repository's radio-testflight.yml workflow reuses existing signing secrets in place. A Radio-specific profile signs `com.radioonlinepro.player`. Credentials are never included in this public package. The standalone public testflight.yml requires separately configured secrets.

## Physical iPhone checks

Play multiple VRT streams; test station switching, pause/resume, reconnect, offline errors, favorites persistence, local search, background/lock-screen playback, headphones, interruptions, AirPlay, sleep timer and accessibility. Station availability and territory restrictions can change.
