# CodeTerm release artifacts

Public mirror for CodeTerm release binaries + the signed Tauri auto-update manifest.

The source repository ([rollacode/codeterm](https://github.com/rollacode/codeterm)) is private.
This mirror exists so the in-app updater can fetch `latest.json` and the platform
binary anonymously.

## Update manifest

`https://github.com/rollacode/codeterm-releases/releases/latest/download/latest.json`

Schema is the standard `tauri-plugin-updater` shape:

```json
{
  "version": "1.1.3",
  "notes": "...",
  "pub_date": "2026-05-02T13:22:40Z",
  "platforms": {
    "darwin-aarch64": { "url": "...", "signature": "<minisign base64>" },
    "darwin-x86_64":  { "url": "...", "signature": "<minisign base64>" },
    "windows-x86_64": { "url": "...", "signature": "<minisign base64>" }
  }
}
```

## Verifying signatures

Manifests are signed with minisign. Public key (also baked into the app's
`tauri.conf.json`):

```
untrusted comment: minisign public key: 90C06D3B044DEFDE
RWTe700EO23AkCc2cUmgTwzbZK/OStZ/EBly9tkVfW6QxW6bBQK3c/Ng
```

Pin this key — never replace it without rotating every installed copy.
