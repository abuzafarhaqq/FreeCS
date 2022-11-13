# Nov 13, 2022: Update

---

### Linux Getting Rusty

Rust is getting big. After Adding Rust to the linux kernel, it'll grow as a big programming language.
Today's tool will be available on Linux and macOS. You can use `alias` to this new tool. If you have `cargo`, the rust package manager, you can install all these using `cargo`.

### Alacrity: Terminal Emulator with GPU support

It is a cross-platform modern terminal emulator with some defaults. It is **GPU accelerated**. All configurations done in **YMAL**.
Install:
```
# Arch Linux
yay -S alacritty
# Fedora/CentOS
dnf copr enable atim/alacritty
dnf install alacritty
# Debian/Ubuntu
add-apt-repository ppa:aslatter/ppa
apt install alacritty
# macOS Homebrew
brew install --cask alacritty
# Windows Scoop
scoop bucket add extras
scoop install alacritty
# Cargo on any
cargo install alacritty
```

### Starship: Prompt Like Oh-My-ZSH

It is terminal prompt. It is fast, highly customizable, have themes, settings just like zsh. It works on Fish, zsh, bash, oh-my-zsh. It works best with NerdFonts.
Install:
```
# Arch
yay -S starship
# Fedora/CentOS
dnf install starship
# Debian/Ubuntu
curl -sS https://starship.rs/install.sh | sh
# macOS/Homebrew
brew install starship
# macOS ports
port install starship
# Windows scoop
scoop install starship
# Cargo
cargo install starship --locked
```

### Bat: Cat replacement tool
It is a replacement tool for cat. Syntax highlight, line numbers, Git change highlight. By default it works like less by paging large output (can be disable). Bat can also be previewer for fzf. It can also be combined with other tools like: tail, man, git etc.
Install:
```
# Arch Linux
yay -S bat
# Fedora/CentOS
dnf install bat
# Debian/Ubuntu
apt install bat
# macOS Homebrew
brew install bat
# macOS MacPorts
port install bat
# Windows Scoop
scoop install bat
# Cargo
cargo install bat --locked
```

### LSD and EXA: LS replacement tool
Both are replacement for `ls`. Both have: Colors, icons, headers, sorting, tree views. Exa is faster than in `lsd` and git support.
Install:
```
# Arch Linux
yay -S exa
yay -S lsd
# Fedora/CentOS
dnf install exa
dnf install lsd
# Debian/Ubuntu
apt install exa
dpkg install lsd.deb # get file from https://github.com/Peltoche/lsd/releases
# macOS Homebrew
bre install exa
bre install lsd
# macOS MacPorts
port install lsd
# Windows Scoop
scoop install lsd
# Cargo
cargo install exa
cargo install lsd

# alias:
alias ls='exa --git --icons --color=always --group-directories-first'
alias ls='lsd --header --color=always --group-directories-first'
```

### rip: Improved Version of RM
`rm` replacement tool is `rip`. It is: faster, safer, user-friendly, remove files to temp-dir (recover using `rip -u`)
Install:
```
# Arch Linux
yay -S rm-improved
# Fedora/CentOS/Debian/Ubuntu
# Install from binary/Build locally using cargo
# macOS Homebrew
bew install rm-improved
# Cargo
cargo install rm-improved
```

### xcp: Partial Clone of cp
`xcp` is partial clone of `cp`. It is: faster, user-friendly, progress-bar, parallel copying, .gitignore support.
Install:
```
# Arch Linux
yay -S xcp
# Fedora/CentOS/Debian/Ubuntu/macOS
# Install from binary/Build locally using cargo
# Cargo
cargo install xcp

# Alias
alias cp='xcp'
```

### zoxide: cd Replacement Tool
`zoxide` is `cd` replacement tool. It can: remembers visited dirs, jump visited dir(without full path), partial path support, interactive selection using fzf.
Install:
```
# Arch Linux
yay -S zoxide
# Fedora/CentOS
dnf install zoxide
# Debian/Ubuntu
apt install zoxide
# macOS Homebrew
brew install zoxide
# macOS MacPorts
port install zoxide
# Windows Scoop
scoop install zoxide
# Cargo
cargo install zoxide --locked

# After installing, add this to shell config.
# bash (~/.bashrc)
eval "$(zoxide init bash)"
# zsh (~/.zshrc)
eval "$(zoxide init zsh)"
# fish (~/.config/fish/config.fish)
zoxide init fish | source

# Alias:
alias cd='z'
```

### dust: DU replacement tool
`dust` is an alternative for the `du command`. It is: fast, better UX, nice visualization for Disk Usage.
Install:
```
# Arch Linux
yay -S dust
# Fedora/CentOS
# Install from github.com/bootandy/dust/releases
# Debian/Ubuntu
deb-get install du-dust
# macOS Homebrew
brew install dust
# macOS MacPorts
port install dust
# Windows Scoop
scoop install dust
# Cargo
cargo install du-dust --locked
```

### ripgrep : replacement for grep

`ripgrep(rg)` line oriented search tool, recursively search your current dir for regex pattern. It has: compressed files search, colorized output, smart case, file type filtering, multi-threading, understands: .gitignore files, skips hidden and ignored files.
Install:
```
# Arch Linux
yay -S ripgrep
# Fedora/CentOS
dnf install ripgrep
# Debian/Ubuntu
apt-get install ripgrep
# macOS Homebrew
brew install ripgrep
# macOS MacPorts
port install ripgrep
# Windows Scoop
scoop install ripgrep
# Cargo
cargo install ripgrep
```

### fd: alternative to find
`fd` is an alternative to `find`. It is: parallel traversing, colorized, patterns, regex, parallel commands, smart case, understands .gitignore files.
Install:
```
# Arch Linux
yay -S fd
# Fedora/CentOS
dnf install fd-find
# Debian/Ubuntu
apt-get install fd-find
# macOS Homebrew
brew install fd
# macOS MacPorts
port install fd
# Windows Scoop
scoop install fd
# Cargo
cargo install fd-find
```

### sd: replacement for sed, awk
`sd` is a find and replace CLI, replacement for `sed`, `awk`. Faster than `sed`
Install:
```
# Arch Linux
yay -S sd
# Fedora/CentOS
dnf install sd
# Debian/Ubuntu
# install from release page
# macOS Homebrew
brew install sd
# Windows Scoop
scoop install sd-cli
# Cargo
cargo install sd
```

### procs: replacement for ps
`procs` replace `ps`. It gives: colorized human-readable output, multi-column search, more info than `ps`, docker support(show docker container names for the process running docker container), paging, watch mode, tree view, Filer by(name, PID), use logical and/or operators to combine multiple filters.
Install:
```
# Arch Linux
yay -S procs
# Fedora/CentOS
dnf install procs
# Debian/Ubuntu
# install from release page
# macOS Homebrew
brew install procs
# macOS MacPorts
prot install procs
# Windows Scoop
scoop install procs
# Cargo
cargo install procs
```

### bottom: top replacement
`bottom` replaces `top` with nice terminal UI. It is: feature rich, customizable.
Install:
```
# Arch Linux
yay -S bottom
# Fedora/CentOS
dnf copr enable atim/bottom -y
dnf install bottom
# Debian/Ubuntu
# install from release page
# macOS Homebrew
brew install bottom
# macOS MacPorts
prot install bottom
# Windows Scoop
scoop install bottom
# Cargo
cargo install bottom --locked
```

### topgrade: system up-to-dater
`topgrade` detects most of the package managers and triggers updates. It is configurable(can be ignore certain package managers). It can detect: pacman, SDKMAN, Flatpack, snap, Homebrew, rustup, Linux firmware, pip etc. It is cross-platform(Windows, macOS, Linux).
Install:
```
# Arch Linux
yay -S topgrade
# Fedora/CentOS
# Debian/Ubuntu
# Install binary from release page.
# macOS Homebrew
brew install topgrade
# macOS MacPorts
prot install topgrade
# Windows Scoop
# Cargo
cargo install topgrade --locked
```

### broot: tree alternative
`broot` is `tree` alternative can be used to navigate file structure and it respects to .gitignore. You can `cd` into dir from the tree view, open sub-dirs in a panel and even preview files.
Install:
```
# Arch Linux
yay -S broot
# Fedora/CentOS
# Debian/Ubuntu
# Install binary from release page.
# dystroy.org/broot/install/
# macOS Homebrew
brew install broot
# macOS MacPorts
prot install broot
# Windows Scoop
# Cargo
cargo install broot --locked
```

### tokei: count lines and stats of code
`tokei` can count lines and stats of code. It is: accurate, nice output, support 150 language, can output in: JSON, YMAL, CBOR, human-readable tables.
Install:
```
# Arch Linux
yay -S tokei
# Fedora/CentOS
dnf install tokei
# Debian/Ubuntu
# Install binary from release page.
# macOS Homebrew
brew install tokei
# macOS MacPorts
prot install tokei
# Windows Scoop
scoop install tokei
# Cargo
cargo install tokei
```

Other notable tools:
- [kdash: simple dashboard for kubernetes](github.com/kdash-rs/kdash)
- [zellij: terminal multiplexer with batteries included](github.com/zellij-org/zellij)
- [nushell: shell written in rust](github.com/nushell/nushell)
- [xh: HTTPie alternative with better performance](github.com/ducaale/xh)
- [monolith: convert any webpage into single HTML file with all assets inlined](github.com/y2z/monolith)
- [delta: Syntax Highlighting pager for git, diff, grep output](github.com/dandavison/delta)
- [ripsecrets: Find secret keys in your code before commit to git](github.com/sirwart/ripsecrets)
- [eva: CLI REPL calculator](github.com/nerdypepper/eva)
- [List of other Rust CLI tools](https://gist.github.com/sts10/daadbc2f403bdffad1b6d33aff016c0a)


Gets more rusty my pc! Thank you everyone! Peace
