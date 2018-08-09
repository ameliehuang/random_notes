##git update a fork from the original repo

###1. check the current remote of the fork repo in the local clone:
git remote -v
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)

###2. add the original/parent repo as the remote for the fork repo in the local clone:
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git

###3. recheck the current remote of the fork repo in the local clone:
git remote -v
origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)

###4. featch the changes in the original/parent repo:
git fetch upstream
remote: Counting objects: 75, done.
remote: Compressing objects: 100% (53/53), done.
remote: Total 62 (delta 27), reused 44 (delta 9)
Unpacking objects: 100% (62/62), done.
From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
 * [new branch]      master     			   -> upstream/master
 * [new branch]      develop                   -> upstream/develop

###5. checkout the local branch
git checkout develop
Switched to branch 'develop'

###6. merge the changes from the upstream/develop into local develop branch. This will bring the changes from the upstream repo into the local fork's branch and merge with any local changes.
git merge upstream/develop

Auto-merging yam-client-raptor-parent/yam-client-spring-integration/pom.xml
Auto-merging yam-client-raptor-parent/yam-client-spring-automation/src/test/resources/protected/protected.cfg
...

###7. update the fork repo on GitHub with the changes:
git push

##intellij
###"Maven: Failed to read artifact descriptor" on projects with child/parent modules
1. You can always try mvn -U clean install
-U Forces a check for updated releases and snapshots on remote repositories

2. In intellij
   - Go to File
   - Select Settings
   - Select Build, Execution, Deployments
   - Select Build Tools from drop down
   - Select Maven from drop down
   - Tick the Always update snapshots check box
