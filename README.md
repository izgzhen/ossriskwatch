# OSS Risk Watch

A list of new & interesting OSS code.

## npm

[@instrument/storytime-react-scripts@3.0.0-storytime-1](https://www.npmjs.com/package/@instrument/storytime-react-scripts/v/3.0.0-storytime-1)

```
./package/scripts/eject.js:const execSync = require('child_process').execSync;
./package/scripts/eject.js:    let stdout = execSync(`git status --porcelain`, {
./package/scripts/test.js:const execSync = require('child_process').execSync;
./package/scripts/test.js:    execSync('git rev-parse --is-inside-work-tree', { stdio: 'ignore' });
./package/scripts/test.js:    execSync('hg --cwd . root', { stdio: 'ignore' });
./package/scripts/init.js:const execSync = require('child_process').execSync;
./package/scripts/init.js:    execSync('git rev-parse --is-inside-work-tree', { stdio: 'ignore' });
./package/scripts/init.js:    execSync('hg --cwd . root', { stdio: 'ignore' });
./package/scripts/init.js:    execSync('git --version', { stdio: 'ignore' });
./package/scripts/init.js:    execSync('git init', { stdio: 'ignore' });
./package/scripts/init.js:    execSync('git add -A', { stdio: 'ignore' });
./package/scripts/init.js:    execSync('git commit -m "Initial commit from Create React App"', {
```
