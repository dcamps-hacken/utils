# USEFUL COMMANDS

## Update Github Token:
1. Go to terminal and type the following (this will store the credentials when a new git operation is performed):
```
git config --global credential.helper store
```
2. Clone a repo so that credentials are stored --> introduce new credentials

Run specific test in Foundry:
```
forge test --match-test <test-name>
```


Count LOC:
```
cloc --by-file --include-lang=Solidity . //count al solidity files
cloc --by-file --include-lang=Solidity --exclude-dir=_mocks,interfaces . //exclude some folders
```

## SOLIDITY FRAMEWORKS

### SOLCOVER

In order to skip files from coverage score, create a file `.solcover.js` with:
```
module.exports = {
  skipFiles: ['<folder_name>']
};
```
If this does not work at first, run `npx hardhat clean` before coverage --> `yarn` may be needed <br>

When there is `stack too deep` problem, create a `.solcover.js` file with the following:
```
module.exports = {
  configureYulOptimizer: true
};
```

### FOUNDRY

New project:
```
forge install
forge build
forge coverage
```


### HARDHAT

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
In order to install a different OZ version use:
```
yarn add --dev @openzeppelin/contracts@v3.2.0
```

### TRUFFLE
Install @openzeppelin/contracts
```
npm install @openzeppelin/contracts
```

Run tests: <br>
1. Open new terminal in VSCode and run `ganache`
2. In VSCode terminal write `truffle tests --network <network-name>`

Run coverage: <br>
1. Install compatible branch of solidity-coverage with `npm i git://github.com/sc-forks/solidity-coverage.git#0.8.x-truffle --save`
2. Add plugin into `truffle-config.js` as `plugins: ['solidity-coverage'],`
3. Run `truffle run coverage`

### GANACHE
Install globally:
```
npm install -g ganache
```
#### Run tests on mainnet:
1. Fork ETH mainnet using Infura in working directory:
```
ganache-cli --fork https://mainnet.infura.io/v3/PUT_INFURA_KEY_HERE
```
2. In parallel, open a new terminal in working directory. Run console on forked mainnet:
```
yarn truffle console --network mainnet_fork
```
This will open a truffle console.
<br> 3. In truffle console, run `test`

### BROWNIE

eth-brownie package version of the npm:
```
@openzeppelin-contracts
```

## SECURITY ANALYZER TOOLS

### MYTHX

Install mythx-cli
```
pip install mythx-cli
```
api-key
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI0ODE2OThjNi1jMzgyLTQ0MzMtOTE3My0wM2I3YzViNzhhZTciLCJpYXQiOjE2NjY4Nzc4MjYuMzU4LCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODI0NTM4MjYuMzQyLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.K7lCHnRXXDHRb7Aj3GsXghnHGwcnwLZ4HfYF_nDcL-Y
```

#### Run Mythx on Terminal 
1. Go to project root folder

2. Create a group and get the findings --> re-run the command once the analysis ended in order to get the results again (it will not compute all)
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

7. Analyze a specific file:
```
mythx --api-key eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI0ODE2OThjNi1jMzgyLTQ0MzMtOTE3My0wM2I3YzViNzhhZTciLCJpYXQiOjE2NjY4Nzc4MjYuMzU4LCJpc3MiOiJNeXRoWCBBdXRoIFNlcnZpY2UiLCJleHAiOjE5ODI0NTM4MjYuMzQyLCJ1c2VySWQiOiI2MmQ1M2E3YTVlYzQ5NDgwOTBjODQyYWEifQ.K7lCHnRXXDHRb7Aj3GsXghnHGwcnwLZ4HfYF_nDcL-Y analyze --mode deep --remap-import "@openzeppelin/=node_modules/@openzeppelin/" --remap-import "@gnosis.pm/=node_modules/@gnosis.pm/" contracts/ArtMarketplace/ArtMarketplace.sol
```

8. Solidity Compilver version flag:
```
--solc-version TEXT 
```

### SLITHER

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
Flag to ignore compilation in Truffle
```
--truffle-ignore-compile
```
Run slither and print summary table
```
slither . --print human-summary
```
Foundry run with remaps and filters:
```
slither . --solc-remaps "@openzeppelin/=lib/openzeppelin-contracts/contracts/ solady/=lib/solady @openzeppelin-contracts/=lib/openzeppelin-contracts/"
```
Config file can be set as `slither.config.json` in root folder:
```
{
  "filter_paths": "lib|test|script|openzeppelin|openzeppelin-contracts|solady",
  "solc_remaps": [
    "@openzeppelin/contracts-upgradeable/=lib/openzeppelin-contracts-upgradeable/contracts/",
    "@openzeppelin/contracts/=lib/openzeppelin-contracts/contracts/",
    "solady/=lib/solady/"
  ]
}
```


### SOLC-SELECT

- `solc-select versions`: Display installed versions <br>
- `solc-select install`: Prints available versions to install <br>
- `solc-select use 0.8.9`: Switch global version to 0.8.9

## GIT
- `git clone <url>`: clone repo <br>

#### Manage cloned repo
- `git status`: What's going on <br>
- `git log`: Show history of the commits, hashes and comments <br>
- `git remote`: Show the name of the server linked to the repo (usually origin) <br>
- `git remote -v`: Shows the URL of the server linked to the repo <br>
- `git remote set-url origin <url-of-new-repo>`: Change the URL of the server linked to the repo <br>
- `git show -s`: Show current commit <br>
- `git show`:	Show current commit + changes <br>
- `git checkout -b <branch-name> 6e559cb`: Create a new branch at commit '6e559cb' and moves to it <br>

#### Move among branches and commits 
- `git branch`: Show the branch you are currently working <br>
- `git branch -D <branch-name>`: Delete branch <br>
- `git checkout -b <branch-name>`: Create a new branch and moves to it <br>
- `git checkout <branch-name>`: Switch to another branch <br>
- `git checkout -b <branch-name> 6e559cb`: Create a new branch at commit '6e559cb' and moves to it <br>

#### Create a commit 
- `git add <filename>`: Add file to next commit <br>
- `git add .`: Add the whole directory to next commit <br>
- `git commit -m "description of the commit changes"`: Update local repository <br>
- `git commit -am "description of the commit changes"`: Add and commit all files <br>
- `git push`: Update Github servers from local repository <br>
- `git push --set-upstream origin <branch-name>`: Make a new local branch and push those changes since the server is not aware of this new branch
- `git pull`: Update local repository from Github servers <br>

#### Reverts
- `git revert <commit to revert>`: Revert a commit <br>
- `git reset --hard <commit-hash>`: Revert last commit <br>
- `git reset --hard origin/master`  <br>

#### Identify user 
In order to set the name and password globally <br>
1- Use the folliwing command:
```
git config --global credential.helper cache
```
2- Clone a repo and enter the name and github `token` --> they will be remain stored!

#### Pull Request 
Request to merge the current branch with the main > done through the GitHub web on the branch with changes
=> GitHub allows to set permissions and requests regarding mergings and changes


#### Merge
`git merge <branch-name>`: Merge current branch with main

Conflict between local change and servir change when we use a `git pull` => manual change + commit has to be done to fix it
e.g. 
```
a = 1
// <<<<<<<<<<<< HEAD
b = 2  => represents our local changes
//=======
b = 0  => represents server (remote) changes
// >>>>>>>>>>>>>>>> 892382356374891714718 => numbes represent commit hash (unique identifier)
```

## NODEJS
use `nvm` --> download via `homebrew` <br>
- `nvm ls`: get the list of downloaded versions <br>
- `nvm use <version>` : use a specific version <br>
- `nvm install <version>` : install and use specific version



## UBUNTU

`Alt + ImpPant + B`: reboot
