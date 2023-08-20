# serde_optout_unification_proof

Repro at top-bin directory

```
top-bin]$ rm -rf target ; cargo build
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
$ rm -rf target ; cargo build --features from_source
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
```

from_source should feature unify so it gets built from source from top-bin