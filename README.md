# launcher-chunks

Content-addressed chunk store for central-launcher payload updates, served as static files.

A [desync](https://github.com/folbricht/desync) store is a directory of chunks
named by their hash, so any static file host is one. A client holding an older
payload reuses the chunks it already has and fetches only the ones the new
version adds — nothing here computes a delta, so one published copy serves every
client whatever version it is coming from.

## Use

    central-launcher update <index> <dest> <seed> \
      https://raw.githubusercontent.com/V-Sekai-fire/datasource-launcher-chunks/main/main/store

`v1.caibx` and `v2.caibx` are fixtures: two 20 MB payloads differing by one
byte. Extracting v2 with v1 as the seed takes 294 of 295 chunks from the seed
and one from here.
