# Git Notes

* git push origin master
* git config --global user.name "name"
* git config --global user.email "email"

* Branch
> git branch -r\
> git fetch origin Production\
> git checkout Production

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
> git revert --no-commit commit-id..HEAD\
> git commit

[Back to Contents](../README.md)
