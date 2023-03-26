# act-overlays

Curated machine readable list of FFXIV OverlayPlugin Overlays

[Propose new Overlays](https://github.com/cking/act-overlays/issues/new/choose)!

overlays.json is available at [overlays.json](https://cking.github.io/act-overlays/overlays.json)

You have a simple URL Builder at [overlay_url_builder.html](https://cking.github.io/act-overlays/overlay_url_builder.html)

## Schema

Schema current version is 2.

### Main fields

- `name`: Name of the overlay. Required.
- `uri`: URI pointing to the overlay. Should be using a secure protocols such as HTTPS. Should be preferred when the parsing server uses a secure protocol (`wss://`). Required.
- `plaintext_uri`: Alternative URI pointing to the overlay. Must be using a plaintext HTTP protocol. Commonly used by overlays to connect to local plaintext WebSockets. Should be preferred when the parsing server uses an plaintext protocol (`ws://`). Optional.
- `suggested_width`, `suggested_height`: Suggested dimensions for the overlay on creation. Optional.
- `features`: List of features of the overlay. Optional.

### Features

- `cactbot`: Requires the presence of cactbot event handlers.
- `overlay_ws`: Requires an HTTP GET parameter `OVERLAY_WS` to be added pointing to the WebSocket URI of the parse server endpoint. Some overlays do not support URI encoding and it is recommended not to use it. Example: `http://foobar.com/?OVERLAY_WS=ws://localhost:12345/ws`. Incompatible with `host_port`.
- `host_port`: Legacy setting. Requires an HTTP GET parameter `HOST_PORT` to be added pointing to the URL of the parse server endpoint. Some overlays do not support URI encoding and it is recommended not to use it. Example: `http://foobar.com/?HOST_PORT=ws://localhost:12345`. Note that this should not contain any path component as the overlay will replace it with hardcoded values. Incompatible with `overlay_ws`.
- `system`: System configuration overlay. Overlay managers can chose not to list those and prefer a dedicated UI instead.