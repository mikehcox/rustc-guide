# Documenting rustc

You might want to build documentation of the various components
available like the standard library. There’s two ways to go about this.
 You can run rustdoc directly on the file to make sure the HTML is
 correct, which is fast. Alternatively, you can build the documentation
 as part of the  build process through x.py. Both are viable methods
 since documentation  is more about the content.

## Document everything

```ignore
./x.py doc
```

## If you want to avoid the whole Stage 2 build

```ignore
./x.py doc --stage 1
```

First the compiler and rustdoc get built to make sure everything is okay
and then it documents the files.

## Document specific components

```ignore
./x.py doc src/doc/book
./x.py doc src/doc/nomicon
./x.py doc src/doc/book src/libstd
```

Much like individual tests or building certain components you can build only
 the documentation you want.

## Document internal rustc items

Compiler documentation is not built by default. There's a flag in
config.toml for achieving the same.
But, when enabled, compiler documentation does include internal items.

Next open up config.toml and make sure these two lines are set to true:

```toml
docs = true
compiler-docs = true
```

When you want to build the compiler docs as well run this command:

```ignore
./x.py doc
```

This will see that the docs and compiler-docs options are set to true
and build the normally hidden compiler docs!

### Compiler Documentation

The documentation for the rust components are found at [rustc doc].

[rustc doc]: https://doc.rust-lang.org/nightly/nightly-rustc/rustc/
