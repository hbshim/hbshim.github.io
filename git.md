$ git init

$ git add *.c
$ git add LICENSE
$ git add README test.rb LICENSE

$ git commit -m 'initial project version'
$ git commit
$ git commit -m "Story 182: Fix benchmarks for speed"
$ git commit -a -m 'added new benchmarks'
$ git commit --amend
$ git clone --bare my_project my_project.git
$ git clone user@git.example.com:/opt/git/my_project.git
$ git init --bare --shared

$ git clone https://github.com/libgit2/libgit2
$ git clone https://github.com/libgit2/libgit2 mylibgit
$ git clone https://github.com/schacon/simplegit-progit

$ git status
$ git status -s

$ git diff
$ git diff --staged
$ git diff --cached

$ git rm --cached README
$ git rm log/\*.log
$ git rm \*~

$ git mv file_from file_to

$ git log
$ git log -p -2
$ git log --stat
$ git log --pretty=oneline
$ git log --pretty=format:"%h - %an, %ar : %s"
$ git log --pretty=format:"%h %s" --graph
$ git log --since=2.weeks
$ git log -Sfunction_name
$ git log --pretty="%h - %s" --author=gitster --since="2008-10-01" \
$ git log --pretty=oneline
$ git log --oneline --decorate
$ git log --oneline --decorate --graph --all

$ git reset HEAD CONTRIBUTING.md
$ git reset HEAD -- fileA

$ git checkout -- CONTRIBUTING.md
$ git checkout -b version2 v2.0.0
$ git checkout -b iss53
$ git checkout -b hotfix
$ git checkout -b serverfix origin/serverfix
$ git checkout -b sf origin/serverfix
$ git checkout testing
$ git checkout master
$ git checkout experiment
$ git checkout serverfix
$ git checkout iss53
$ git checkout --track origin/serverfix

$ git remote
$ git remote -v
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote show origin
$ git remote rename pb paul
$ git remote rm paul
$ git remote add local_proj /opt/git/project.git

$ git fetch [remote-name]
$ git fetch origin

$ git push origin master
$ git push origin v1.5
$ git push origin --tags
$ git push origin serverfix
$ git push origin --delete serverfix

$ git tag
$ git tag -l "v1.8.5*"
$ git tag -a v1.4 -m "my version 1.4"
$ git tag -a v1.2 9fceb02
$ git tag v1.4-lw

$ git show v1.2
$ git show v1.4
$ git show v1.4-lw

$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
$ git config --global alias.unstage 'reset HEAD --'
$ git config --global alias.last 'log -1 HEAD'
$ git config --global alias.visual '!gitk'

$ git unstage fileA

$ git last

$ git branch testing
$ git branch iss53
$ git branch -d hotfix
$ git branch -d iss53
$ git branch -d testing
$ git branch
$ git branch -u origin/serverfix
$ git branch -v
$ git branch -vv
$ git fetch --all
$ git branch --merged
$ git branch --no-merged

$ git merge hotfix
$ git merge iss53
$ git merge experiment

$ git mergetool

$ git ls-remote (remote)

$ git remote show (remote)

$ git pull

$ git rebase master
$ git rebase master server
$ git rebase --onto master server client

