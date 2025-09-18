# VoiceInk Build Configuration

## Development Build Setup

This project has been configured for easy development builds without code signing issues.

### What Was Changed

The Debug configuration in `VoiceInk.xcodeproj/project.pbxproj` has been modified to:

```
CODE_SIGN_IDENTITY = "";
CODE_SIGNING_REQUIRED = NO;
```

### Building the Project

Now you can build the project simply with:

```bash
# Standard build command (no extra flags needed)
xcodebuild -scheme VoiceInk -configuration Debug build

# Or using Xcode GUI
# Just press Cmd+B or Product > Build
```

### Running the App

The built app will be located at:
```
/Users/work/Library/Developer/Xcode/DerivedData/VoiceInk-*/Build/Products/Debug/VoiceInk.app
```

### Notes

- **Debug builds**: No code signing required, builds immediately
- **Release builds**: Still configured with original signing settings for distribution
- **Entitlements warning**: You'll see a warning about entitlements without signing, but this doesn't affect functionality
- **Security prompts**: macOS may show security warnings on first launch (normal for unsigned apps)

### Dependencies

The project automatically resolves these Swift Package Manager dependencies:
- KeyboardShortcuts
- LaunchAtLogin  
- Sparkle
- FluidAudio
- MediaRemoteAdapter
- Zip

Plus the whisper.xcframework for local transcription.

### Original Issue

Previously, builds would fail with:
```
"VoiceInk" requires a provisioning profile. Select a provisioning profile in the Signing & Capabilities editor.
```

This has been resolved by disabling code signing for Debug builds while keeping Release builds ready for proper distribution.
