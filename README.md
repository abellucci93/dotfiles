# dotfiles

This repository uses **[GNU Stow](https://www.gnu.org/software/stow/)** to manage and symlink your configuration files (dotfiles) across systems in a simple, maintainable, and scalable way.

## Why use this setup?

This dotfiles approach is inspired by the article [**Never Lose Your Configs Again**](https://typecraft.dev/tutorial/never-lose-your-configs-again) by [Typecraft](https://typecraft.dev).

It provides a great breakdown of using GNU Stow to manage dotfiles effectively — highly recommended reading.

## Repository structure

This repo follows a strict naming convention required by Stow.

Each config or tool (e.g. `zsh`, `tmux`) is stored in its own directory ("package") and mirrors the file’s path starting from your `$HOME`.

Example:

```txt
dotfiles/
├── zshrc/
│   └── .zshrc
├── tmux/
│   └── .tmux.conf
```

## Installing Your Configs

1. **Clone this repository**

```bash
git clone https://github.com/abellucci93/dotfiles.git ~/dotfiles
cd ~/dotfiles
```

2. **Install GNU Stow** (if you haven't already)

* Debian/Ubuntu: `sudo apt install stow`
* macOS (with Homebrew): `brew install stow`

3. **Stow your configs**

```bash
stow <package-name>
```

Examples:

```bash
stow zshrc         # links .zshrc to your home directory
stow tmux          # links .tmux.conf to your home directory
stow */            # symlinks everything (glob only for directories)
```

## Adding a new config

To add a new config:

1. Create a folder in your dotfiles directory with a descriptive name:

```bash
mkdir -p kitty/.config/kitty
```

2. Move your current config into it:

```bash
mv ~/.config/kitty/* dotfiles/kitty/.config/kitty/
```

3. From the `dotfiles` root, run:

```bash
stow kitty
```

## Resources

* [GNU Stow Documentation](https://www.gnu.org/software/stow/)
* [Never Lose Your Configs Again](https://typecraft.dev/tutorial/never-lose-your-configs-again)
