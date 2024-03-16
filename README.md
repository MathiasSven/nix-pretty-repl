# Nix Pretty Repl

*This is potentially deprecated, since as of Nix 2.21 pretty [printing is builtin](https://github.com/NixOS/nix/pull/9931)*

---

A fork simply for the purpose of adding pretty printing to the Repl (`:pp`). It is based on [nixfmt-flib](https://github.com/MathiasSven/nixfmt-flib), a fork of [nixfmt](https://github.com/serokell/nixfmt) that adds FFI and some (not so pretty) changes to make sure no functionality is lost in the Repl such as color codes and unshowable expressions such as `«derivation ...»`.

The default package has been changed to:
```nix
writeScriptBin "nix-repl" ''
  ${nix} repl $@
'';
```

This fork also enables `ReplFlake` by default (C/P from [this](https://github.com/privatevoid-net/nix-super/commit/cb263a33b9a14c8e99018af663e02b95e66659bd) commit). So this should be a streight replacement to the normal `nix repl`

## Vi Mode

Nix already has a configuration flag that allows building with `readline` instead of `editline`, this fork enables that by default, meaning that you can get `vi` keybindings by adding `set editing-mode vi` to `~/.inputrc` if you desire, or toggle it while in the repl via `C-M-j` (`Ctrl-Alt-j`).

In theory you should be able to use `vi` mode on nix with `editline` by adding `bind -v` to `~/.editrc`, however I was not able to reproduce that. 

## Note

Obviously this is super inefficient, as in you download and build a whole different clone just to use `nix repl`, but for me it is simpler to use it like this vs figuring out how to decouple the repl from the rest.
