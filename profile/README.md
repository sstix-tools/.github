# sstix-tools

Personal command-line utilities, script packages, and autoloadable Zsh functions — released as **APT**, **RPM**, and **Nix** packages.

Registry: [sstix-tools/registry](https://github.com/sstix-tools/registry) · [https://sstix-tools.github.io/registry/](https://sstix-tools.github.io/registry/)

## Install

**APT (Debian / Ubuntu)**
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://sstix-tools.github.io/registry/sstix-tools.gpg | sudo tee /etc/apt/keyrings/sstix-tools.gpg > /dev/null
echo "deb [signed-by=/etc/apt/keyrings/sstix-tools.gpg] https://sstix-tools.github.io/registry/apt stable main" | sudo tee /etc/apt/sources.list.d/sstix-tools.list
sudo apt update && sudo apt install <package-name>
```

**RPM (Fedora / RHEL / openSUSE)**
```bash
sudo tee /etc/yum.repos.d/sstix-tools.repo <<'EOF'
[sstix-tools]
name=sstix-tools Repository
baseurl=https://sstix-tools.github.io/registry/rpm
enabled=1
gpgcheck=1
gpgkey=https://sstix-tools.github.io/registry/sstix-tools.asc
EOF
sudo dnf install <package-name>
```

**Nix**
```bash
nix run github:sstix-tools/<package-name>          # from the tool repo
nix run github:sstix-tools/registry#<package-name> # via the registry aggregator
```

## Zsh

Add to `~/.zshrc` so packaged functions and completions are picked up:

```zsh
export PATH="$HOME/.local/bin:$PATH"
fpath=("$HOME/.local/share/zsh/functions" "$HOME/.local/share/zsh/site-functions" $fpath)
autoload -Uz compinit && compinit
```

## New tools

Create a repo from one of the templates, then tag a release (`v1.0.0`) — the release pipeline builds `.deb` / `.rpm` / `.tar.gz` and re-indexes the registry automatically.

| Template | Use for |
|---|---|
| [template-bash-utility](https://github.com/sstix-tools/template-bash-utility) | Bash / POSIX scripts |
| [template-python-utility](https://github.com/sstix-tools/template-python-utility) | Python CLI scripts |
| [template-c-utility](https://github.com/sstix-tools/template-c-utility) | Compiled C (Makefile) |
| [template-zsh-function](https://github.com/sstix-tools/template-zsh-function) | Autoloadable Zsh functions |

Full docs, secrets setup, and GPG key info: [registry README](https://github.com/sstix-tools/registry#readme).
