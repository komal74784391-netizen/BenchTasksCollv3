# Pipeline notes

The legacy shard writer uploads a copy of every bundle file under
`bundles/<release_tag>/` and then rewrites it in place. If the rewrite
fails, the slot keeps whatever the download proxy returned (in practice
a short JSON error document), so the size of a file under `bundles/`
can be far smaller than the payload it is named after. The payload
bytes themselves are content-addressed under `.store/blobs/`.
