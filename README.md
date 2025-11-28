# flutter_application_1

A new Flutter project with Codemagic CI/CD integration.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## Codemagic CI/CD Setup for iOS

This project is configured with Codemagic CI/CD for automated iOS builds. The configuration file `codemagic.yaml` includes two workflows:

### iOS Workflow (Release)
- Builds release IPA for App Store distribution
- Automatically increments build number
- Submits to TestFlight
- Runs Flutter analyze and tests

### iOS Debug Workflow
- Builds debug IPA for development
- Useful for testing and development purposes

### Setup Instructions

1. **Sign up for Codemagic**: Go to [codemagic.io](https://codemagic.io) and sign up with your repository provider

2. **Add your repository**: Connect your Git repository to Codemagic

3. **Configure iOS code signing**:
   - Go to your Codemagic app settings
   - Navigate to "Code signing identities"
   - Add your Apple Developer certificates and provisioning profiles
   - Or use Codemagic's automatic code signing feature

4. **Update the configuration**:
   - Edit `codemagic.yaml` and update:
     - `BUNDLE_ID`: Your app's bundle identifier (currently: `com.example.flutterApplication1`)
     - `APP_STORE_APPLE_ID`: Your app's Apple ID from App Store Connect
     - Email recipients for build notifications
     - Beta testing groups if using TestFlight

5. **Set up App Store Connect integration** (for automatic publishing):
   - In Codemagic, go to "Teams" > "Integrations"
   - Add App Store Connect API key
   - This enables automatic TestFlight submission and build number management

6. **Trigger a build**:
   - Push to your repository
   - Or manually trigger from Codemagic dashboard

### Configuration Details

- **Flutter version**: Stable channel
- **Xcode version**: Latest available on Codemagic
- **Instance type**: Mac mini M2 for faster builds
- **Max build duration**: 120 minutes

### Artifacts

After each build, the following artifacts are available:
- IPA file (`build/ios/ipa/*.ipa`)
- Xcode build logs
- Flutter logs

### Additional Resources

- [Codemagic Documentation](https://docs.codemagic.io/)
- [Flutter iOS Deployment](https://docs.flutter.dev/deployment/ios)
- [App Store Connect API](https://developer.apple.com/app-store-connect/api/)
