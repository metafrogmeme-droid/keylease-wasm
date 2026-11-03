# keylease-wasm

Prebuilt WASM files for KeyLease on NEAR testnet, published so OutLayer can fetch them by URL.
OutLayer only runs bytes whose sha256 matches the hash named on chain, so check the hashes below.

| File                  | Bytes  | sha256                                                             | What                                    |
| --------------------- | ------ | ------------------------------------------------------------------ | --------------------------------------- |
| `keylease-proxy.wasm` | 426133 | `95385bd10e778f8f1488a266abaa79c455347f6404f53140b3bde8755a4cd970` | KeyLease proxy (`scripts/build-proxy.sh`) |
| `proxy-a.wasm`        | 77394  | `856a37d8ccc2aa28af7ce96914948821cfd0ca938184f0384b9c7338067d5d1c` | Spike build A (`spike/build.sh`)        |
| `proxy-b.wasm`        | 77394  | `17ce3c3352af16cb2412e9397ec6b84a6ef493775cfc3afa2704fc1e1bc1b515` | Spike build B (`spike/build.sh`)        |

Source: `metafrogmeme-droid/keylease` at commit `0e45d5b`. Built with rustc 1.99.1 (pinned, paths
remapped), target `wasm32-wasip2`. No source code, keys or config live here, only the build outputs.

## Verify

```sh
sha256sum -c SHA256SUMS
```

Rebuild from source and compare:

```sh
git clone https://github.com/metafrogmeme-droid/keylease && cd keylease && git checkout 0e45d5b
scripts/build-proxy.sh   # prints: rustc 1.99.1 / keylease-proxy.wasm 426133 bytes / sha256 95385bd1…cd970
spike/build.sh           # writes spike/artifacts/proxy-a.wasm and proxy-b.wasm
```

## License

MIT, see `LICENSE`.
