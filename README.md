# sample-tracing-rust

Rust tracing example

# Running application

Please update Basic Authentication key, organization, and stream-name information in below function in [main.rs](OtlpHttpSpanExporter), you can find this information by navigating to ingestion -> custom -> traces -> OTEL Collector.

```rs
fn otl_metadata() -> Result<MetadataMap, Error> {
    let mut map = MetadataMap::with_capacity(3);

    map.insert(
        "authorization",
        format!("Basic cm9vdEBleGFtcGxlLmNvbTprVUZ2SmpDYjRibjZMcUZo") // This is picked from the Ingestion tab OpenObserve
            .parse()
            .unwrap(),
    );
    map.insert("organization", "default".parse().unwrap());
    map.insert("stream-name", "default".parse().unwrap());
    Ok(map)
}
```

This sample program uses OtlpGrpcSpanExporter.

---

Run the application

```shell
cargo run
```

The trace should be collected by OpenObserve and searchable as shown below
