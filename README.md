# Nix Pretty Repl
A fork simply for the purpose of adding pretty printing to the Repl (`:pp`). It is based on [nixfmt-flib](https://github.com/MathiasSven/nixfmt-flib), a fork of [nixfmt](https://github.com/serokell/nixfmt) that adds FFI and some (not so pretty) changes to make sure no functionality is lost in the Repl such as color codes and unshowable expressions such as `«derivation ...»`.

The default package has been changed to:
```nix
writeScriptBin "nix-repl" ''
  ${nix} repl $@
'';
```

This fork also enables `ReplFlake` by default (C/P from [this](https://github.com/privatevoid-net/nix-super/commit/cb263a33b9a14c8e99018af663e02b95e66659bd) commit). So this should be a streight replacement to the normal `nix repl`

## Note

Obviously this is super inefficient, as in you download and build a whole different clone just to use `nix repl`, but for me it is simpler to use it like this vs figuring out how to decouple the repl from the rest.
