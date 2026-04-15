# flutter-tvos Engine Artifacts

Pre-built Flutter engine binaries for tvOS, targeting **Flutter 3.41.4**.

These artifacts are consumed automatically by the
[flutter-tvos](https://github.com/fluttertv/flutter-tvos) CLI via
`flutter-tvos precache`. You do not need to download them manually.

---

## Artifacts

| File | Target | Use |
|------|--------|-----|
| `tvos_debug_sim_arm64.zip` | Simulator arm64 | Debug builds on tvOS Simulator |
| `tvos_debug_arm64.zip` | Device arm64 | Debug builds on physical Apple TV |
| `tvos_profile_arm64.zip` | Device arm64 | Profile builds on physical Apple TV |
| `tvos_release_arm64.zip` | Device arm64 | Release builds on physical Apple TV |
| `host_debug_unopt.zip` | macOS host | Dart frontend compiler (debug) |
| `host_release.zip` | macOS host | Dart frontend compiler (release) |

Each zip contains:
- `Flutter.framework` / `Flutter.xcframework` — pre-built tvOS Flutter framework
- `flutter_patched_sdk` — Dart SDK patched for Flutter
- `clang_arm64/gen_snapshot` — AOT compiler (device variants only)
- `clang_arm64/impellerc` — Impeller shader compiler
- Host variants include `gen_snapshot` and `gen/frontend_server_aot.dart.snapshot`

---

## Usage

```bash
# Automatic (recommended)
flutter-tvos precache

# Custom source
export TVOS_ENGINE_BASE_URL=https://github.com/fluttertv/engine-artifacts/releases/download/v1.0.0-flutter3.41.4
flutter-tvos precache
```

---

## Flutter Version

Based on Flutter `3.41.4` with tvOS support.  
Deployment target: **tvOS 13.0+**  
Architecture: **arm64**

---

## License

The engine source is BSD 3-Clause licensed. See
[THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md) for required attribution
notices from Flutter and Liberty Global.
