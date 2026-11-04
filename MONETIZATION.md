# Advertising integration — 4 November 2026

Google Mobile Ads 13.12.0 and UMP 3.1.0 are pinned through official Swift packages. The banner is above the catalog selector, separated from playback controls. No interstitial, rewarded, audio-interrupting ad, Firebase Analytics or purchase is included.

## Current state

Commercial ads are OFF. The AdMob account was created and is under Google verification. The European consent message is published in English and Romanian, with a refusal button in all regions. RTB creative consent checking is enabled and legitimate-interest choices are not enabled by default. The Info.plist now contains the real Radio Online Pro app and banner IDs created in the owner's AdMob account. Explicit test mode still requests only Google's test banner ID. Both RadioCommercialRightsConfirmed and RadioPublisherSetupComplete are false. Launch makes no ad or consent request in this configuration. About & privacy offers an explicit Google test banner; it cannot earn revenue. Stopping it removes the view. Consent errors do not disable radio.

## Production release prerequisites

1. Obtain express commercial permission for included broadcasters or replace the catalog with streams licensed for advertising-supported use. VRT URL publication does not establish commercial rights. Keep evidence and territories in RIGHTS.md.
2. In the owner's Google AdMob account, add Radio Online Pro as an unpublished iOS app (bundle com.radioonlinepro.player). Create an adaptive banner ad unit. Complete publisher/payment verification and any required agreement personally or with explicit action-time authorization.
3. Configure European regulations and applicable US/state privacy messages in AdMob Privacy & messaging. Review age/audience settings before launch. Do not declare child-directed status without a concrete audience assessment.
4. Replace GADApplicationIdentifier and RadioBannerAdUnitID with the actual publisher app/unit IDs. Never use sample IDs to claim production readiness. Set RadioPublisherSetupComplete only after account/privacy setup is verified. Set RadioCommercialRightsConfirmed only after evidence in step 1 exists.
5. Publish the exact app-ads.txt line provided by that AdMob account at the root of the developer website declared in the App Store listing. Do not invent a publisher ID. Verify Google's crawl. No app-ads.txt is claimed to exist yet.
6. Update App Store privacy labels against Google's current disclosure guide and actual configuration. Nonpersonalized does not mean no data collection. Include IP-derived location, device identifiers, product/ad interactions and diagnostics as applicable. The bundled Google SDK privacy manifests do not replace App Store labels.
7. Run simulator tests and device consent/ad tests with test devices. Never click live ads. Verify portrait layout, no-fill/offline behavior, consent changes, screen reader, interruptions and background playback. Rebuild and select the new binary for App Review.
8. After Apple publishes the app, link its actual public App Store listing to AdMob. Google initiates app readiness review; no agent can grant approval. Apple paid-app tax/bank completion does not configure Google advertising payouts.

COMMERCIAL_PERMISSION_REQUEST_DRAFT.md contains an unsent permission request for the broadcaster.

A vendor-manifest worksheet is provided in PRIVACY_DISCLOSURE_DRAFT.md. It is not a completed App Store privacy submission.

Sources: https://developers.google.com/admob/ios/quick-start ; https://developers.google.com/admob/ios/privacy ; https://developers.google.com/admob/ios/banner ; https://support.google.com/admob/answer/10564477

The exact app-ads.txt line supplied by AdMob is hosted at https://valentinnedelcu1974-arch.github.io/app-ads.txt and was checked for HTTPS 200 and exact content. The App Store developer website must be associated with this domain and Google must crawl/verify it. That association and crawler verification are not claimed. ADVERTISING_ACCOUNT_SETUP.json records the actual identifiers and status; these identifiers are public configuration, not credentials. No broadcast-rights email has been sent.

US privacy choices message is also published. Build 5 with the actual registered AdMob identifiers passed simulator CI and was uploaded successfully to Apple. Apple web session expired before processing/group status could be rechecked. No live ad requests or revenue enabled.
