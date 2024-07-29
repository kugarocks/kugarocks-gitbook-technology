# 🖥️ macOS env

## Keyboard

System Preferences

* [x] Key Repeat: Fast
* [x] Delay Until Repeat: Short
* [x] Modifier Keys: Caps Lock -> Escape

```
defaults write -g ApplePressAndHoldEnabled -bool false
```

Shortcuts

* [x] App Shortcuts, +
  * [x] All Applications, Zoom, CMD+M
  * [x] All Applications, Minimize, CMD+H
  * [x] Chrome, Bookmark This Tab/Tab..., CMD+L
  * [x] Chrome, Open Location..., CMD+D
  * [x] Chrome, Downloads, SHIFT+CMD+D
* [x] Input Sources
  * [x] Select the previous input source, CMD+E
* [x] Spotlight
  * [x] Show Spotlight search: OPTION+SPACE
  * [x] [Install Alfred](https://www.alfredapp.com/)

## iTerm2

[Terminal emulator for macOS.](https://iterm2.com/)

Preferences config

* [x] Search -> Dim inactive split panes
* [x] Search -> Global key bindings, +
  * Select Split Pane Above, CMD+I
  * Select Split Pane on Left, CMD+J
  * Select Split Pane Below, CMD+K
  * Select Split Pane on Right, CMD+L

## Oh My Zsh

Installation command

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Custom Alias:

```
# custom aliases
alias zsh='vim ~/.zshrc'
alias q='exit'
alias s='sudo'
alias v='vim'
alias g='git'
alias ga='git add'
alias gc='git checkout'
alias gs='git status'
alias gd='git diff'
alias sv='sudo vim'
alias sc="source ~/.zshrc"
alias ..='cd ..'
alias cls='clear'
alias nano="vim"
alias tailf="tail -f"
alias lf='ll -p | grep -v /'
alias ldir='ls -ld -- */'
```

## HSTR

[Easily view, navigate and search your command history.](https://github.com/dvorka/hstr)

```
brew install hstr
```

Configure HSTR just by running:

```
hstr --show-zsh-configuration >> ~/.zshrc
```

## Git Config

Replace name, email, GitHub user.

```
[user]
	name = kuga
	email = kuga@cestbon.mbp

[alias]
        pr = pull --rebase
        br = branch -avv
        ci = commit
        co = checkout
	cm = checkout master
	mg = merge
        st = status
        l = log --color --graph --pretty=format:'%Cred%h%Creset -%C(bold yellow)%d%Creset %s %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit
        accept-ours = "!f() { files=\"$@\"; [ -z $files ] && files='.'; git checkout --ours -- $files; git add -u $files; }; f"
        accept-theirs = "!f() { files=\"$@\"; [ -z $files ] && files='.'; git checkout --theirs -- $files; git add -u $files; }; f"
        diffeol = diff --ignore-space-at-eol

[core]
        excludesfile = /Users/hairdresser/.gitignore

[color]
        branch = auto
        diff = auto
        status = auto

[GitHub]
        user = kuga

[credential]
	helper = osxkeychain

[pull]
	rebase = false// Some code
```

## Kubernetes

[kubectl: The Kubernetes command-line tool.](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)

```
brew install kubectl
```

[kubectx: Switch between contexts & namespaces.](https://github.com/ahmetb/kubectx)

```
brew install kubectx
```

Add the following to your `.zshrc` file:

```
# kubectx
alias kc="kubectx"
alias kn="kubens"

KUBECTX_CURRENT_FGCOLOR=$(tput setaf 6)
```

[kube-ps1: Kubernetes prompt for bash and zsh.](https://github.com/jonmosco/kube-ps1)

```
brew install kube-ps1
```

Add the following to your `.zshrc` file:

```
# kube-ps1
# https://github.com/jonmosco/kube-ps1
# todo change source path
source /usr/local/Cellar/kube-ps1/0.7.0/share/kube-ps1.sh
PROMPT='$(kube_ps1)'$PROMPT
KUBE_PS1_PREFIX="["
KUBE_PS1_SUFFIX="]"
KUBE_PS1_SYMBOL_ENABLE=false
KUBE_PS1_CTX_COLOR="83"
KUBE_PS1_NS_COLOR="201"
```

[kubectl-aliases: Convenient shell aliases for kubectl.](https://github.com/ahmetb/kubectl-aliases)

Download [.kubectl\_aliases](https://raw.githubusercontent.com/ahmetb/kubectl-aliases/master/.kubectl\_aliases) file & Add the following to your `.zshrc` file:

```
# load kubectl aliases file
[ -f ~/.kubectl_aliases ] && source ~/.kubectl_aliases

# Print the full command before running it
function kubectl() { echo "+ kubectl $@">&2; command kubectl $@; }
```
