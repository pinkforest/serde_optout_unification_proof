# serde_optout_unification_proof

Repro at top-bin directory

```
$ rm -rf ../target ; cargo build --features from_source
   Compiling proc-macro2 v1.0.66
   Compiling unicode-ident v1.0.11
   Compiling quote v1.0.33
   Compiling syn v2.0.29
   Compiling serde_derive v1.0.183 (/home/foobar/code/serde/precompiled/serde_derive)
   Compiling some-lib v0.1.0 (/home/foobar/code/serde_optout_unification_proof/some-lib)
   Compiling top-bin v0.1.0 (/home/foobar/code/serde_optout_unification_proof/top-bin)
    Finished dev [unoptimized + debuginfo] target(s) in 2.97s
[foobar@localhost top-bin]$ rm -rf ../target ; cargo build
   Compiling serde_derive v1.0.183 (/home/foobar/code/serde/precompiled/serde_derive)
   Compiling some-lib v0.1.0 (/home/foobar/code/serde_optout_unification_proof/some-lib)
   Compiling top-bin v0.1.0 (/home/foobar/code/serde_optout_unification_proof/top-bin)
    Finished dev [unoptimized + debuginfo] target(s) in 0.33s
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