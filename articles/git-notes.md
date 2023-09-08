# Git Notes

* git push origin master
* git config --global user.name "name"
* git config --global user.email "email"

* Branch
> git branch -r\
> git fetch origin Production\
> git checkout Production\
> git branch \<branch-name> \<commit-number>\
> delete local branch: git branch -d \<branch_name>\
> delete remote branch: git push \<remote_name> --delete \<branch_name>

* Tags
> git tag # show all tags\
> git tag -a r1.0 -m "Release 1.0" # create tag\
> git show r1.0\
> git push origin r1.0\
> git checkout r1.0

* Add SSH key to GitHub
> ssh-keygen -t rsa -C "email" -b 4096\
> xclip -sel clip < ~/.ssh/id_rsa.pub\
> paste it in the SSH setting of GitHub

* Remote
> git remote -v\
> git remote rename origin gitlab\
> git remote remove gitlab\
> git remote add origin git@bitbucket.org::ohmio/ground-segmentation.git

* Submodule
> git submodule add git@bitbucket.org::ohmio/common_libraries.git folder-name\
> git submodule update --init --recursive\
> git submodule update --recursive --remote

* Revert to a previous commit
> git revert --no-commit "commit-id"..HEAD\
> git commit

* Reset head
> git reset --hard \<commit-SHA>\
> git push origin HEAD:\<name-of-remote-branch>

* View commit
> gitk \<commit>

* Log
> git log --pretty=format:"%h %ad %s"\
> git log --graph --oneline --decorate --all

* history of file
> gitk -- \<path-to-file>\
> git log -p -- \<path/to/file>

* compare two commits
> git diff commit1 commit2\
> git tui diff commit1 commit2


[Back to Contents](../README.md)
