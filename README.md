# Generate shapes

```
git clone https://github.com/ProjectZKM/Ziren.git
cd Ziren
```

## Full generation

```
WORKLOADS=(
    "../ziren-shape-bin/chess"
    "../ziren-shape-bin/fibonacci-1k"
    "../ziren-shape-bin/fibonacci-10k"
    "../ziren-shape-bin/fibonacci-100k"
    "../ziren-shape-bin/fibonacci-1m"
    "../ziren-shape-bin/fibonacci-10m"
    "../ziren-shape-bin/fibonacci-100m"
    "../ziren-shape-bin/json"
    "../ziren-shape-bin/sha2-100kb"
    "../ziren-shape-bin/sha2-1mb"
    "../ziren-shape-bin/sha2-10mb"
    "../ziren-shape-bin/ssz-withdrawals"
    "../ziren-shape-bin/tendermint"
)

RUST_LOG=info cargo run --release -p zkm-prover --bin find_maximal_shapes -- \
--shard-sizes "17 18 19 20 21" \
--list "${WORKLOADS[*]}"

RUST_LOG=info cargo run --release -p zkm-prover --bin find_small_shapes -- \
--maximal-shapes-json "maximal_shapes.json" \
--log2-memory-heights "17 18 19 20 21"
```

## Incremental Generation​​

```
WORKLOADS=(
    "../ziren-shape-bin/chess"
    "../ziren-shape-bin/fibonacci-1k"
    "../ziren-shape-bin/fibonacci-10k"
    "../ziren-shape-bin/fibonacci-100k"
    "../ziren-shape-bin/fibonacci-1m"
    "../ziren-shape-bin/fibonacci-10m"
    "../ziren-shape-bin/fibonacci-100m"
    "../ziren-shape-bin/json"
    "../ziren-shape-bin/sha2-100kb"
    "../ziren-shape-bin/sha2-1mb"
    "../ziren-shape-bin/sha2-10mb"
    "../ziren-shape-bin/ssz-withdrawals"
    "../ziren-shape-bin/tendermint"
)

RUST_LOG=info cargo run --release -p zkm-prover --bin find_maximal_shapes -- \
--initial "maximal_shapes.json" \
--shard-sizes "17 18 19 20 21" \
--list "${WORKLOADS[*]}"

RUST_LOG=info cargo run --release -p zkm-prover --bin find_small_shapes -- \
--maximal-shapes-json "maximal_shapes.json" \
--log2-memory-heights "17 18 19 20 21"
```
