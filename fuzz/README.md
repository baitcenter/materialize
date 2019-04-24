WIP fuzzing. Not super useful yet.

## Fuzzing sqllogictest

Before first use:

``` sh
cd materialize
cargo install cargo-fuzz
cp -ar sqllogictest/test/ fuzz/corpus/fuzz_sqllogictest/
cargo +nightly fuzz cmin fuzz_sqllogictest
```

To fuzz stuff:

``` sh
cd materialize
cargo +nightly fuzz run fuzz_sqllogictest -- -workers=4
```

Failing tests are added to `./fuzz/artifacts/fuzz_sqllogictest` and can be rerun with `cargo test -p sqllogictest`.

TODO(jamii) figure out why sqllogictest::test::fuzz_artifacts can't be run by name

## Fuzzing testdrive

Before first use:

``` sh
cd materialize
cargo install cargo-fuzz
cp -ar test/* fuzz/corpus/fuzz_testdrive
```

To fuzz stuff:

``` sh
cd materialize
cargo +nightly fuzz run fuzz_testdriver
```

Failing tests are added to `./fuzz/artifacts/fuzz_testdrive` and can be rerun with `cargo run --bin testdrive ./fuzz/artificats/fuzz_testdrive/<FAILING_TEST>`.