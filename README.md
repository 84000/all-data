# all-data
A conglomerate of 4 other data-* repos (as submodules)

The way to clone these to collaboration server is as follows:
```sh
cd /home/existdb
git clone --recursive git@github.com:84000/all-data.git exist-sync
```

Further docs on submodules in git: https://github.blog/2016-02-01-working-with-submodules/

# How to make new commits to this repo
The nature of this repo is that it serves as a common container for its 4 submodules while not having files of its own.
So any change introduced is a change to one of its submodules. As these changes amass, we would naturally want to have a new _release commit_ of the all-data repo. This is how to do it:

CD into the base dir of your all-data repo then issue the following 4 commands:
```sh
git submodule update --recursive --remote
git add .
git commit -m "<commit message here>"
git push
```

Then anyone cloning the repo with `git clone --recursive git@github.com:84000/all-data.git` will get the new state of the submodules.

If you also want to make each of your submodules track its master branch (not needed unless you plan to cd into a submodule's dir, change some files and commit them), this is the way to do it:
```sh
git submodule foreach --recursive git checkout master
```
