# 可能用到的软件
- [zoxide](https://github.com/ajeetdsouza/zoxide)
- [bat](https://github.com/sharkdp/bat)
- [fzf](https://github.com/junegunn/fzf)
- gvim

# 主要配置

```bash
mkcd() {
    mkdir -p "$1" && z "$1"
}
bak() {
    cp -r "$1" "$1.bak"
}
function cdls() {
    builtin cd "$1"&&ls
}

# 多关键词文件搜索函数
function ff {
    if [ $# -eq 0 ]; then
        echo "用法: ff keyword1 [keyword2 ...]"
        return 1
    fi

    # 构造 find 命令
    cmd="find . -type f"
    for kw in "$@"; do
        cmd="$cmd -iname '*$kw*'"
    done
    # 执行并高亮输出
    eval "$cmd" | grep -i --color=auto -E "$*|$"
}

export PATH=$PATH:path_to_bat
export PATH=$PATH:path_to_zoxide
export PATH=$PATH:path_to_fzf
eval "$(zoxide init bash)" # --cmd cd
zx() {
  local query="$*"
  local dir

  dir=$(zoxide query --list --score | \
    fzf --filter="$query" --no-sort | \
    fzf \
      --prompt="zoxide > " \
      --nth=2.. \
      --ansi \
      --height=60% \
      --info=inline \
      --border=rounded \
      --layout=reverse \
      --preview-window=down:40%:wrap \
      --preview='ls -F -C --color=always {2..}' \
      --bind 'ctrl-z:ignore,btab:up,tab:down,enter:become:echo {2..}' \
      --cycle \
      --keep-right \
      --tabstop=1
  )

  [[ -n "$dir" ]] && cd "$dir"
}

alias cnow='mkdir qzkrvp'
alias znow='z qzkrvp && ..'
alias g="gvim"
alias grts="gvim --remote-tab-silent"
alias gvd="gvimdiff"
alias ~='z'
alias gc='gvim ~/.bashrc && read -p "Press ENTER to source .bashrc..." && source ~/.bashrc'
alias grep='grep --color=auto'
alias color_pwd='echo -e "\e[1;37m$(\pwd)\e[0m"'
alias cls="clear && color_pwd && ls"
alias .='cls'
alias ..='z ..'
alias ...='z ../..'

export PS1="\[\e[1;33m\]\u@\h\[\e[m\] \[\e[1;36m\]~>\[\e[m\] "
```
