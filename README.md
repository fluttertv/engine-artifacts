# flutter-tvos Engine Artifacts

Pre-built Flutter engine binaries for tvOS, one release per engine commit.

These artifacts are consumed automatically by the
[flutter-tvos](https://github.com/fluttertv/flutter-tvos) CLI via
`flutter-tvos precache`. You do not need to download them manually: each
flutter-tvos release pins the engine commit it was tested against in
`bin/internal/engine.version`, and the CLI fetches that release from here.

---

## Releases

Every release is tagged `engine-<sha>`, the commit of the
tvOS engine that produced it, and its title names the Flutter version the engine
was built from. The tag is a commit rather than a Flutter version because one
patch set can serve several Flutter releases; a SHA names what was actually
built. The flutter-tvos [CHANGELOG](https://github.com/fluttertv/flutter-tvos/blob/main/CHANGELOG.md)
links each CLI release to the engine release it uses.

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

The artifacts are published unsigned. `flutter-tvos` signs the engine on your
machine with your own certificate on every device build; see
[Code signing](https://github.com/fluttertv/flutter-tvos#code-signing).

---

## Usage

```bash
# Automatic (recommended)
flutter-tvos precache

# Custom source: a mirror, or an engine you built yourself
export TVOS_ENGINE_BASE_URL=https://github.com/fluttertv/engine-artifacts/releases/download/engine-<sha>
flutter-tvos precache
```

---

## Platform

Architecture: **arm64**, for both devices and the simulator.
Rendering: **Impeller on Metal** (tvOS has no OpenGL).
Apps created by flutter-tvos target **tvOS 15.0** and later.

---

## License

The engine source is BSD 3-Clause licensed. See
[THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md) for required attribution
notices from Flutter and Liberty Global.
