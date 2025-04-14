# ~/.zsh_aliases
# Author: David L. Haines 
# Purpose: DevOps-focused ZSH alias collection

##########################
# 🧼 General Shortcuts
##########################
alias cls='clear'
alias ll='ls -lh'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias reload='source ~/.zshrc'

##########################
# 🐍 Python
##########################
alias python='python3'
alias pip='pip3'
alias venv='python3 -m venv venv && source venv/bin/activate'

##########################
# ⚙️ Ansible
##########################
alias av='ansible-vault'
alias ap='ansible-playbook'
alias ai='ansible-inventory'
alias an='ansible'
alias ag='ansible-galaxy'
alias ac='ansible-config'
alias ad='ansible-doc'
alias ansible-pull-latest='ansible-pull -U https://git.example.com/repo.git'

##########################
# 🧰 GitHub CLI (gh)
##########################
alias ghst='gh auth status'
alias ghme='gh auth login'
alias ghco='gh repo clone'
alias ghpr='gh pr create --fill'
alias ghview='gh repo view --web'
alias ghissue='gh issue list --state open'

#########################
# 📚 GitHub (git)
#########################
alias agit='alias | grep -i git'
# gaa = 'git add --all'
# gca = 'git commit --verbose --all'
# gp = 'git push'
# gpd = 'git push --dry-run'
# gss = 'git status --short'
# gst = 'git status'

##########################
# 🔍 ripgrep (rg) Aliases
##########################
alias rg='rg --smart-case --colors=path:fg:green --colors=match:fg:yellow'
alias rgf='rg --files'                            # List files
alias rgp='rg --pcre2'                            # Enable advanced regex
alias rgpy='rg --glob "*.py"'                     # Search only Python files
alias rglog='rg --glob "*.log"'                   # Search logs
alias rgi='rg -i'                                 # Case-insensitive
alias rgs='rg --stats'                            # Show stats
alias rgd='rg --files | xargs dirname | sort | uniq'  # List unique directories
alias rgx='rg -t py -g "!tests/*"'                # Exclude test folder in Python search

##########################
# 🕰️ History Exploration
##########################
alias hist='fc -ln -100'
alias hgrep='history | grep'
alias hsort='history | sort | uniq -c | sort -nr | head -n 20'
alias htop='history | awk "{CMD[\$2]++} END { for(a in CMD)print CMD[a] \" \" a}" | sort -rn | head'

# timestamped history with command numbers
alias hts='history 0 | awk '\''{print strftime("%F %T", $1), $2, $3, $4, $5}'\'''

##########################
# 🐳 Docker
##########################
alias dps='docker ps'
alias dpa='docker ps -a'
alias dcu='docker-compose up -d'
alias dcd='docker-compose down'
alias dbash='docker exec -it'
alias dlogs='docker logs -f'

##########################
# 📦 Tar/Gzip Utils
##########################
alias untar='tar -xvf'
alias tgz='tar -czvf'
alias unzip='unzip -l'

##########################
# 🌐 Networking
##########################
alias myip='curl ifconfig.me'
alias ports='netstat -tulanp'
alias pingg='ping google.com'

##########################
# 📁 File Navigation
##########################
alias cdlog='cd /var/log'
alias cdweb='cd /var/www/html'
alias cdtmp='cd /tmp'

##########################
# 🔧 System Monitoring
##########################
alias dfh='df -h'
alias duh='du -sh *'
alias psg='ps aux | grep -v grep | grep'
alias cpu='top -o %CPU'
alias mem='top -o %MEM'

##########################
# 📋 Misc Utilities
##########################
alias now='date +"%Y-%m-%d %H:%M:%S"'
alias wgetp='wget --progress=bar'
alias json='python3 -m json.tool'
alias qfind='find . -type f -name'  # Usage: qfind "*.conf"
alias bc='batcat '
alias glzsh='glow ~/Public/opensource-cheats/zsh_aliases.md'

