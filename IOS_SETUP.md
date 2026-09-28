# iOS / iPhone deployment

The project is configured for:

- App name: `نظام الحضور`
- Bundle ID: `com.alfath.attendance`
- Codemagic workflow: `ios-testflight`
- Codemagic App Store Connect integration name: `alfath_app_store_connect`

## 1. Apple Developer

1. Join the Apple Developer Program.
2. In Certificates, Identifiers & Profiles, create an App ID:
   `com.alfath.attendance`.
3. In App Store Connect, create a new app using the same Bundle ID.
4. In App Store Connect > Users and Access > Integrations, create an API key
   with App Manager access. Download the `.p8` file and keep its Key ID and
   Issuer ID secure. Never add this file or its values to Git.

## 2. Codemagic

1. Open Team settings > Integrations > Developer Portal.
2. Add the App Store Connect API key with this exact name:
   `alfath_app_store_connect`.
3. Add or generate an Apple Distribution certificate and an App Store
   provisioning profile for `com.alfath.attendance`.
4. Ensure `package-lock.json`, `package.json`, `codemagic.yaml`, and the `www`
   directory are committed and pushed.
5. Start the `iOS TestFlight` workflow.

Codemagic will create the iOS project, add the location and file-sharing
privacy settings, sign the app, build an IPA, and upload it to TestFlight.

## 3. TestFlight

After Apple finishes processing the build:

1. Open App Store Connect > the app > TestFlight.
2. Complete any encryption/export-compliance questions if Apple asks.
3. Add internal testers.
4. Install Apple's TestFlight app on the iPhone and accept the invitation.

## Before App Store review

- Add screenshots, privacy details, support URL, and app description.
- Provide Apple with a working reviewer account.
- Explain that location is required at the moment of attendance check-in and
  check-out.
- Test location permission, GPS-disabled blocking, notifications, PDF/Excel
  sharing, Arabic layout, and safe-area spacing on a real iPhone.
