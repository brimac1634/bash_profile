# bash_profile

####################
##### ALIASES ######
####################

#list out command history in folder
alias hs='history | grep'

#color mode
alias lh='ls -lhaG'

#navigation
alias desk='cd ~/Desktop'

#website navigation
alias bit='open https://bittrex.com'
alias bin='open https://www.binance.com/en'

#application aliases
alias sublime='open -a Sublime\ Text'
alias wx='open -a wechatwebdevtools'
alias sql='brew services start postgresql'
alias sqlstop='brew services stop postgresql'

#.bash_profile aliases
alias edit="open ~/.bash_profile"
alias load="source ~/.bash_profile"

#npm aliases
alias npmupdate='npm install npm@latest -g'
alias upack='npm-check-updates -u && npm update'


###############################
### ENVIRONMENTAL VARIABLES ###
###############################

OFFWHITE="\[\e[38;5;255m\]"
LIGHTBLUE="\[\e[38;5;069m\]"
PURPLE="\[\e[38;5;170m\]"


parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

export PS1="${LIGHTBLUE}\u ${PURPLE}\W${OFFWHITE}\$(parse_git_branch) \[\033[0m\]$ "

export CLICOLOR=1;
export LSCOLORS=exfxcxdxbxegedabagacad;

#Homebrew
export PATH=/usr/local/bin:$PATH

#Flutter
export PATH="$PATH:/Users/brianmacpherson/flutter/flutter/bin"

#NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion


####################
##### FUNCTIONS ######
####################


# Starts recording the simulator.
function recsim() {
    xcrun simctl io booted recordVideo "$1"
}

# opens files in sublime
function sub() {
	open -a Sublime\ Text "$1"
}

#open in text editor
function text() {
	open -a TextEdit "$1"
}

############
##. Git. ###
############

#add, commit, and push
function acp() {
	git add . && git commit -m "$1" && git push
}

#add and commit
function ac() {
	git add . && git commit -m "$1"
}

#checkout
function ch() {
	git checkout "$1"
}

alias br='git branch'
alias st='git status'
alias lg='git log'
