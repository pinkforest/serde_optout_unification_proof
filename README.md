# serde_optout_unification_proof

Repro at top-bin directory

```
top-bin]$ rm -rf target ; cargo build
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
$ rm -rf target ; cargo build --features from_source
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
```

from_source should feature unify so it gets built from source from top-bin

Structure

```
$ cargo tree
top-bin v0.1.0 (/home/foobar/code/serde_optout_unification_proof/top-bin)
└── some-lib v0.1.0 (/home/foobar/code/serde_optout_unification_proof/some-lib)
    └── serde_derive v1.0.183 (proc-macro) (/home/foobar/code/serde/precompiled/serde_derive)
[build-dependencies]
└── some-build-lib v0.1.0 (/home/foobar/code/serde_optout_unification_proof/some-build-lib)
    └── serde_derive v1.0.183 (proc-macro) (/home/foobar/code/serde/precompiled/serde_derive)
```

Have the PR in ../../serde path to prove it works with resolver="2" via feature unification