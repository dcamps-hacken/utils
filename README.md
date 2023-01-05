# git-commands

## SOLC-SELECT

Display installed versions
```
solc-select versions
```
Prints available versions to install
```
solc-select install
```
Switch global version to 0.8.9
```
solc-select use 0.8.9		
```

## NODEJS
Change version of node to 18.12.0
```
sudo n 18.12.0
``` 


## HARDHAT

1. Install hardhat to current directory
```
yarn add --dev hardhat
```
2. Start hardhat
```
yarn hardhat
```
3. Install @openzeppelin/contracts
```
yarn add --dev @openzeppelin/contracts
```

## TRUFFLE
Install @openzeppelin/contracts
```
npm install @openzeppelin/contracts
```


## BROWNIE

eth-brownie package version of the npm:
```
@openzeppelin-contracts
```

## MYTHX

Install mythx-cli
```
pip install mythx-cli
```
api-key
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI0ODE2OThjNi1jMzgyLTQ0MzMtOTE3My0wM2I3YzViNzhhZTciLCJpYXQiOjE2NjY4Nzc4MjYuMzU4LCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODI0NTM4MjYuMzQyLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.K7lCHnRXXDHRb7Aj3GsXghnHGwcnwLZ4HfYF_nDcL-Y
```

### Run Mythx on Terminal 
1. Go to project root folder

2. Create a group and get the findings
```
mythx --api-key eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJiMzNiMjBhNC01NjRlLTQ5NjItYTBlMy1hNzY2N2YyY2NmZjciLCJpYXQiOjE2NjkyMDgxMDQuNzcxLCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODQ3ODQxMDQuNzUzLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.sI7-9dyL7TTSO_x60bBvq5wu1uZ6UCD8zAnkVgRNr-k analyze --mode deep --remap-import "@openzeppelin/=node_modules/@openzeppelin/" --group-name "actafi-david" contracts
```


3. Fetch groups
```
mythx --api-key eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJiMzNiMjBhNC01NjRlLTQ5NjItYTBlMy1hNzY2N2YyY2NmZjciLCJpYXQiOjE2NjkyMDgxMDQuNzcxLCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODQ3ODQxMDQuNzUzLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.sI7-9dyL7TTSO_x60bBvq5wu1uZ6UCD8zAnkVgRNr-k group list
```

4. Get group status
```
mythx --api-key eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJiMzNiMjBhNC01NjRlLTQ5NjItYTBlMy1hNzY2N2YyY2NmZjciLCJpYXQiOjE2NjkyMDgxMDQuNzcxLCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODQ3ODQxMDQuNzUzLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.sI7-9dyL7TTSO_x60bBvq5wu1uZ6UCD8zAnkVgRNr-k group status 638dabe326ec940019d8567c
```

5. Get a report after group submission
```
mythx --api-key eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJiMzNiMjBhNC01NjRlLTQ5NjItYTBlMy1hNzY2N2YyY2NmZjciLCJpYXQiOjE2NjkyMDgxMDQuNzcxLCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODQ3ODQxMDQuNzUzLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.sI7-9dyL7TTSO_x60bBvq5wu1uZ6UCD8zAnkVgRNr-k analyze --mode deep --remap-import "@openzeppelin/=node_modules/@openzeppelin/" contracts/Identity.sol
```

6. Get a report from ID:
```
mythx --api-key eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJiMzNiMjBhNC01NjRlLTQ5NjItYTBlMy1hNzY2N2YyY2NmZjciLCJpYXQiOjE2NjkyMDgxMDQuNzcxLCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODQ3ODQxMDQuNzUzLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.sI7-9dyL7TTSO_x60bBvq5wu1uZ6UCD8zAnkVgRNr-k analysis report 02152048-ddba-4b21-a8fe-776e31209c2b
```



## SLITHER

Run slither on current project, excluding OZ
```
slither . --filter-paths "openzeppelin"						
```
Add @openzeppelin path
```
slither ./contracts/base/Referrals.sol --filter-paths "openzeppelin" --solc-remaps @openzeppelin=node_modules/@openzeppelin
```
Exclude naming-convention and external function calls
```
slither . --filter-paths "openzeppelin" --exclude naming-convention,external-function
```


## UBUNTU

Alt + ImpPant + B			> reboot


## GIT

git clone <url>

git remote                                    > show the name of the server linked to the repo (usually origin)
git remote -v                                 > shows the URL of the server linked to the repo 
git remote set-url origin <url-of-new-repo>   > change the URL of the server linked to the repo

git add <filename>  > adds file to next commit
git add .   > adds the whole directory

git commit -m "description of the commit changes"   > updates local repository
git commit -am "description of the commit changes"  > add and commit all files

git show -s						> shows current commit
git show						> shows current commit + changes

git status   > what's going on

git push    > update Github servers from local repository 

git pull    > update local repository from Github servers

git log     > shows history of the commits, hashes and comments

git reset --hard <commit-hash>  > reverts last commit
git reset --hard origin/master  

git revert <commit to revert>

Identify user:
git config --global user.email "you@example.com"
git config --global user.name "Your Name"

BRANCHING

git branch      > shows the branch you are currently working
git branch -D <branch-name>     > deletes the branch

git checkout -b <branch-name>   		> create a new branch and moves to it
git checkout -b <branch-name> 6e559cb		> create a new branch at commit '6e559cb' and moves to it
git checkout <branch-name>      		> switch to another branch


git merge <branch-name>     > merges current branch with main

git push --set-upstream origin <branch-name>    > when we make a local branch and want to push those 
                                                changes since the server is not aware of this new branch

PULL REQUEST 

Request to merge the current branch with the main > done through the GitHub web on the branch with changes
=> GitHub allows to set permissions and requests regarding mergings and changes


MERGE CONFLICTS

Conflict between local change and servir change when we use a "git pull" 
=> manual change + commit has to be done to fix it

e.g. 

a = 1
// <<<<<<<<<<<< HEAD
b = 2  => represents our local changes
//=======
b = 0  => represents server (remote) changes
// >>>>>>>>>>>>>>>> 892382356374891714718 => numbes represent commit hash (unique identifier)
