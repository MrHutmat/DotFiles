# nvm plugin

This plugin adds autocompletions for [nvm](https://github.com/nvm-sh/nvm) — a Node.js version manager. It also
automatically sources nvm, so you don't need to do it manually in your `.zshrc`.

To use it, add `nvm` to the plugins array of your zshrc file:

```zsh
plugins=(... nvm)
```

## Settings

If you installed nvm in a directory other than `$HOME/.nvm`, set and export `NVM_DIR` to be the directory
where you installed nvm.

These settings should go in your zshrc file, before Oh My Zsh is sourced:

- **`NVM_HOMEBREW`**: if you installed nvm via Homebrew, in a directory other than `/usr/local/opt/nvm`, you
  can set `NVM_HOMEBREW` to be the directory where you installed it. For example, on Apple Silicon-based Macs,
  [Homebrew is installed in `/opt/homebrew`](https://docs.brew.sh/Installation). To get the directory where
  nvm has been installed, regardless of chip architecture, use `NVM_HOMEBREW=$(brew --prefix nvm)`.

## Customization

#### Lazy startup

This option will help you to defer nvm's load until you use it to speed-up your zsh startup. This will source
nvm script only when using it, and will create a function for `node`, `npm`, `pnpm`, `yarn`, and the
command(s) specified by `lazy-cmd` option, so when you call either of them, nvm will be loaded and run with
default version. To enable it, you can add this snippet to your zshrc, before Oh My Zsh is sourced:

```zsh
zstyle ':omz:plugins:nvm' lazy yes
```

Then, to define extra commands that will also trigger nvm load, you can use a similar syntax, adding as many
as you want:

```zsh
zstyle ':omz:plugins:nvm' lazy-cmd eslint prettier typescript ...
```

#### `.nvmrc` autoload

If set, the plugin will automatically load a node version when if finds a
[`.nvmrc` file](https://github.com/nvm-sh/nvm#nvmrc) in the current working directory indicating which node
version to load. This can be done, similar as previous options, adding:

```zsh
zstyle ':omz:plugins:nvm' autoload yes
```

To remove the output generated by NVM when autoloading, you can set the following option:

```zsh
zstyle ':omz:plugins:nvm' silent-autoload yes
```

Note: _this will not remove regular `nvm` output_