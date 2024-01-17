alias gs='git status -s'
alias gsu='git status -u'
alias gaa='git add .'
alias gc='git commit -m'
alias gk='git checkout'
alias gkm='git checkout main'
alias gkb='git checkout -b'
alias gp='git push origin main'
alias gpo='git push origin'
alias gpl='git pull origin main'
alias grv='git remote -v'
alias gra='git remote add origin'
alias glog='git log --oneline'
# maven
alias mvn='/d/apache-maven-3.6.2/bin/mvn'
# Visual Studio Code
alias vsc='code src/app'
# Secured Shell to linux
alias sshr='ssh 98.28.129.85 -p 32415 -l gpdoud'
alias sshl='ssh 192.168.1.23 -l gpdoud'
# angular
alias ng-build-prod='ng build --prod --base-href="./"'
alias startng='start ng serve -o'
# functions
gacp() {
    git add . && git commit -m \""$1"\" && git push origin "$2"
}
exec_sql() {
        sqlcmd -S "localhost\sqlexpress" -E -d "$1" -Q "$2"
}
