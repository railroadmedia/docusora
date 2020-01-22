# Compiling Musora Front End Assets

Make sure to pull your branch to the latest changes first to avoid wierd conflicts.

1. cd to /frontend folder in the project (root npm stuff is legacy)
2. npm install
3. npm build
4. commit changes
5. run bash file: ./version.sh
6. push the new tag and commit is created
7. ready for deploy

# Dependency packages updates & publishing

1. cd to dependency package, eg: cd /app/js-helper-functions
2. decide the new package version, current version is in package.json under "version" key
3. https://docs.npmjs.com/updating-your-published-package-version-number
run: npm version new_version
eg: npm version 0.1.4
4. 'npm version' command creates a commit, push it to remote repository: git push origin master
5. auth required for publishing, get user/pass from 1password, then run command: npm adduser
6. to publish the package run command: npm publish
