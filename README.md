# sample-tracing-rust

Rust tracing example

### Build

Please update `authorization`, `organization`, and `stream-name` information in below function in [main.rs](https://github.com/openobserve/sample-tracing-rust/blob/6a7dd0fe59876a6e3c0732ea3c6da323cda2b402/src/main.rs#L36-L48), you can find this information by navigating OpenObserve UI to ingestion -> custom -> traces -> OTEL Collector. 

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

This sample program uses opentelemetry_otlp via grpc.

### Run

```shell
cargo run
```

### Collected in OpenObserve

The trace should be collected by OpenObserve and searchable as shown below
![image](https://github.com/user-attachments/assets/41e6e325-86a7-439c-85da-3aac45d81183)
