# App Store privacy review worksheet

Not submitted or approved. The earlier ad-free privacy description must not be reused for the advertising binary. Optional test advertising is still a data-processing feature.

Evidence: GoogleMobileAds 13.12.0 framework's vendor-signed PrivacyInfo.xcprivacy, inspected 4 November 2026, and https://developers.google.com/admob/ios/privacy/data-disclosure . Keep vendor manifests intact. The app's own manifest describes its local preferences APIs; it does not replace or cancel SDK disclosures.

The vendor manifest declares these categories. Use them as a starting point, then review actual SDK settings and Apple's definitions before saving labels:

| Data category | Linked in vendor manifest | Tracking in vendor manifest | Purposes in vendor manifest |
|---|---|---|---|
| Coarse location | Yes | No | Third-party advertising, developer advertising, analytics |
| Device ID | Yes | Yes | Third-party advertising, developer advertising, analytics |
| Advertising data | Yes | No | Third-party advertising, developer advertising, analytics |
| Product interaction | Yes | No | Third-party advertising, developer advertising, analytics |
| Performance data | No | No | Third-party advertising, developer advertising, analytics |
| Other diagnostic data | No | No | Third-party advertising, developer advertising, analytics |
| Crash data | No | No | Analytics |

This app requests nonpersonalized ads, disables publisher first-party ID, does not request ATT authorization, and does not access IDFA itself. Those settings must be considered alongside Google's broader vendor declarations. Do not infer that all device identifiers, location or SDK analytics disappear, and do not assert a final tracking answer solely from the lack of an ATT prompt. Review UMP, actual network behavior and Apple's cross-app tracking definition before production release. No Firebase Analytics or mediation partners are included.

The developer currently receives no account/login data or radio usage analytics from a developer-operated backend. Favorites and local search remain on device. Broadcaster IP/server processing and support emails are described in PRIVACY.md.
