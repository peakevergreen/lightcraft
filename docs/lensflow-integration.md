# LensFlow browser integration

This fork exposes a browser-only `lensflow_request(action, paramsJson, bytes)` promise interface for a capability-scoped parent workspace. It supports photo import, project restore/snapshot, export, revision status and existing engine commands. The parent owns tenant-scoped persistence and receives bytes rather than filesystem or storage authority.

With `?lensflow=1`, the editor uses an isolated in-memory library and disables browser-local restoration and directory-drop behavior that could mix another studio's files into the project. Standalone browser behavior is preserved. Native LightCraft remains available independently.

Portal tokens and backend storage credentials never enter the editor. The host must verify the exact iframe source, origin, protocol and per-workspace channel, enforce upload limits, and reject stale saves. Project snapshots preserve files and development state; originals stay unchanged.

No model weights or hosting deployment is added. Upstream licenses/notices remain applicable. LensFlow pins the fork commit and packages its browser host and dependency/license inventory separately.
