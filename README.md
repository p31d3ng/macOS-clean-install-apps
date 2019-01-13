# Apps that needs to install
- 1Password (Mac App Store)
- [Karabiner-Element](https://pqrs.org/osx/karabiner/)
- [BetterTouchTool](https://folivora.ai/)
- Paste (Mac App Store)
- Manico (Mac App Store)
- [iTerm2](https://www.iterm2.com/)
- [homebrew](https://brew.sh/)
    - `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
- fish shell `brew install fish`
- [oh-my-fish](https://github.com/oh-my-fish/oh-my-fish)
    - `curl -L https://get.oh-my.fish | fish`
    - `omf install lambda` (theme)
- [VS Code](https://code.visualstudio.com/)
- emacs
    - `brew cask install emacs`
- Spark (Mac App Store)
- [Chrome](https://www.google.com/chrome/)
- [Firefox](https://www.mozilla.org/en-US/firefox/new/)
    - `about:config`
        - `network.trr.mode` set to `3` (DoH only)
        - `network.trr.uri` set to `https://1.1.1.1/dns-query`
- [Bartender 3](https://www.macbartender.com/)
- Moom (Mac App Store)
- Parcel (Mac App Store)
- The unarchiver (Mac App Store)
- Bear (Mac App Store)

# Alias for Fish
```
# Get latest container ID
alias dl="docker ps -l -q"

# Get container process
alias dps="docker ps"

# Get process included stop container
alias dpa="docker ps -a"

# Get images
alias di="docker images"

# Get container IP
alias dip="docker inspect --format '{{ .NetworkSettings.IPAddress }}'"

# Run deamonized container, e.g., $dkd base /bin/echo hello
alias dkd="docker run -d -P"

# Run interactive container, e.g., $dki base /bin/bash
alias dki="docker run -i -t -P"

# Execute interactive container, e.g., $dex base /bin/bash
alias dex="docker exec -i -t"

# alias
alias gcmsg='git commit -m'
alias gp='git push'
alias gd='git diff'
alias gaa='git add -A'
alias gst='git status'
alias cl='clear;ls -al'
alias lc="leetcode"
alias kcg="kubectl config get-contexts"
alias kcu="kubectl config use-context"
alias kgp="kubectl get pods"

# Funcitons
function private_key
   openssl pkcs8 -in $argv -inform PEM -outform DER -topk8 -nocrypt | openssl sha1 -c
end

function clean_docker
  docker rm (docker ps -aq -f status=exited)
  docker rmi (docker images --filter 'dangling=true' -q --no-trunc)
end

function clean_volume
  docker volume rm (docker volume ls -qf dangling=true)
end

function unset
  set --erase $argv
end
```