# bash_profile
personal bash profile



####################
##### ALIASES ######
####################

#list out command history in folder

alias hs='history | grep'

#color mode

alias lh='ls -lhaG'

#navigation

alias desk='cd ~/Desktop'

#git

alias st='git status'
alias lg='git log'

#website navigation

alias bit='open https://bittrex.com'
alias bin='open https://www.binance.com/en'

#project navigation

alias webproj='cd /Users/brianmacpherson/Web\ Dev/Projects'
alias appproj='cd /Users/brianmacpherson/App\ Dev/Projects'
alias tele='cd /Users/brianmacpherson/Desktop/Teleprompter'
alias brian='cd /Users/brianmacpherson/Desktop/brian'
alias nrs='cd /Users/brianmacpherson/WeChatProjects/NetRoadshow'
alias ar='cd /Users/brianmacpherson/Arduino'

#cantotalk nav

alias canto='cd /Users/brianmacpherson/Desktop/CantoTalk'
alias cantoweb='cd /Users/brianmacpherson/Desktop/cantotalkweb'
alias cantoser='cd /Users/brianmacpherson/Desktop/cantoserver'

alias design='cd /Users/brianmacpherson/Web\ Dev/Design\ Content && open .'
alias entries='cd /Users/brianmacpherson/Desktop/Entries && open Entries.numbers'

#application aliases

alias sub='open -a Sublime\ Text'
alias wx='open -a wechatwebdevtools'
alias sql='brew services start postgresql'
alias sqlstop='brew services stop postgresql'

#.bash_profile aliases

alias edit="open ~/.bash_profile"
alias load="source ~/.bash_profile"

#npm aliases

alias npmupdate='npm install npm@latest -g'
alias upack='npm-check-updates -u && npm update'

#flutter

alias iossim='open -a Simulator'
alias flutx='open ios/Runner.xcworkspace'
alias droid='open -a Android\ Studio'


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


# Virtualenv/VirtualenvWrapper

source /usr/local/bin/virtualenvwrapper.sh


####################
##### FUNCTIONS ######
####################

#scrape internet for photos

function getphotos() {
	cd /Volumes/File\ Storage/CantoTalk\ Dataset/Training\ Data && mkdir "$1" && cd ../Testing\ Data/ && mkdir "$1" && cd .. && python search_bing_api.py --query "$2" --output Training\ Data/"$1"
}

# Starts recording the simulator.

function recsim() {
    xcrun simctl io booted recordVideo "$1"
}

# opens files in brackets

function brackets() {
	open -a Brackets "$1"
}

# opens files in sublime

function sublime() {
	open -a Sublime\ Text "$1"
}

#open in text editor

function text() {
	open -a TextEdit "$1"
}

#start new web project on desktop

function newproj() {
	cd ~/Desktop && mkdir "$1" && cd "$1" && touch index.html && touch style.css && touch script.js && sublime .
}

#starts new backend server project

function newback() {
	cd ~/Desktop && mkdir "$1" && cd "$1" && cp ~/globalScripts/server.js . && sublime . && npm init -y && npm install express body-parser bcrypt-nodejs cors && npm install nodemon --save-dev
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

