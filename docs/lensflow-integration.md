# LensFlow browser integration

This fork exposes a browser-only `lensflow_request(action, paramsJson, bytes)` promise interface for a capability-scoped parent workspace. It supports photo import, project restore/snapshot, export, revision status and existing engine commands. The parent owns tenant-scoped persistence and receives bytes rather than filesystem or storage authority.

With `?lensflow=1`, the editor uses an isolated in-memory library and disables browser-local restoration and directory-drop behavior that could mix another studio's files into the project. Standalone browser behavior is preserved. Native LightCraft remains available independently.

Portal tokens and backend storage credentials never enter the editor. The host must verify the exact iframe source, origin, protocol and per-workspace channel, enforce upload limits, and reject stale saves. Project snapshots preserve files and development state; originals stay unchanged.

No model weights or hosting deployment is added. Upstream licenses/notices remain applicable. LensFlow pins the fork commit and packages its browser host and dependency/license inventory separately.

## Fork CI/CD scope

The only active workflow in this fork is `lensflow-web.yml`. It checks Rust
formatting, Clippy against the browser target, browser-safe crates and dependency
layers, then builds optimized WebAssembly and validates compressed download parts.
The uploaded artifact is a CI intermediate; LensFlow separately supplies its host,
wasm-bindgen glue, and complete license notices. This workflow never deploys.

Inherited desktop, platform, documentation, performance, and release workflow
files are retained. Their GitHub workflows are disabled, and each inherited job
also requires the repository variable `ENABLE_NATIVE_EDITOR_WORKFLOWS=true`.
It is currently false. To restore an inherited pipeline later, review its purpose,
set that variable to true, and enable only the desired workflow through GitHub.
Native application code and packaging sources remain available.
