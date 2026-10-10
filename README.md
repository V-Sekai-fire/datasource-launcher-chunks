# datasource-launcher-chunks

A content-addressed chunk store for the central launcher's payload updates, served as static files.

## Use

The store uses the [desync](https://github.com/folbricht/desync) chunk and index format: a directory of chunks named by their hash, so any static file host can serve it. A client that holds an older payload reuses the chunks it has and fetches only the ones a new version adds, so one published copy serves every client whatever version it starts from. `v1.caibx` and `v2.caibx` are fixtures, two payloads that differ by one byte.

## Build and run

[transport-central-launcher](https://github.com/V-Sekai-fire/transport-central-launcher) updates from this store. Fetch through a CDN that mirrors this repository rather than from raw file hosting, which is rate-limited:

```sh
central-launcher update <index> <dest> <seed> https://cdn.jsdelivr.net/gh/V-Sekai-fire/datasource-launcher-chunks/store
```

## Licence

MIT. See [LICENSE](LICENSE). `CITATION.cff` records the licence as MIT.
