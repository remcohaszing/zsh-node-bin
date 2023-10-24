# Zsh node-bin

Recursively add `node_modules/.bin` to your `$PATH`.

## Installation

### Oh My Zsh

Clone the repository into your `OMZ` [custom directory](https://github.com/ohmyzsh/ohmyzsh#custom-directory).

```zsh
git clone https://github.com/remcohaszing/zsh-node-bin.git "${$ZSH:-~/.oh-my-zsh}/custom/plugins/node-bin"
```

In your `.zshrc` file, add `node-bin` to the plugins array,

```zsh
plugins+=(node-bin)
```

### Without Oh My Zsh

Clone the repository somewhere.

```zsh
git clone https://github.com/remcohaszing/zsh-node-bin.git ~/.local/share/zsh-node-bin
```

Source [`node-bin.plugin.zsh`](node-bin.plugin.zsh) in your `.zshrc`

```zsh
source ~/.local/share/zsh-node-bin/node-bin.plugin.zsh
```

## Usage

This plugin runs a function before each command. This function searches for all `node_modules/.bin` directories up the file tree and adds them to your `$PATH`. This allows you to run these commands without the use of `npx`, `pnpx`, or `bunx`. This also works for subdirectories in your project and monorepos.

For example, without this plugin, you would run:

```sh
npx eslint .
pnpx prettier .
yarn remark .
bunx vitest
```

Now you can now run:

```sh
eslint .
prettier .
remark .
vitest
```

This plugin removes the overhead of those command runners, It also means those commands work with other integrations, such as autocompletion and [`thefuck`](https://github.com/nvbn/thefuck).

## Security

This plugin **appends** the paths. This means commands from `node_modules/.bin` can never override your system commands.

## License

[MIT](LICENSE.md) © [Remco Haszing](https://github.com/remcohaszing)
