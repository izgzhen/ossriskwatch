# OSS Risk Watch

A list of new & interesting OSS code.

## npm

We focus on the potential vulnerability that passes variable or high-privilege commands to `execSync` here.

`wix-storybook-utils@3.0.59`

```
./package/docs/make-sections-docs.js:const { execSync } = require('child_process');
./package/docs/make-sections-docs.js:  execSync(typedocCommand);
```

~~`@mindbox%frontend@0.46.64`~~

The commands are all `npm ***` constants. So it should be safe.

```
./package/build/version-bump.js:const execSync = require("child_process").execSync;
./package/build/version-bump.js:const exec = command => execSync(command, { encoding: "utf8" });
```

~~`storybook-chroma@3.5.0`~~

The commands are all `git ***` constants. So it should be safe.

```
./package/bin/__tests__/serializers.test.js:import { execSync } from 'child_process';
./package/bin/__tests__/serializers.test.js:    execSync('some hot garbage');
./package/bin/git/git.js:import { execSync } from 'child_process';
./package/bin/git/git.js:    return execSync(`${command} 2>&1`)
```

`vtex@2.87.2`

```
./package/lib/modules/utils.js:    child_process_es6_promise_1.execSync(command, { stdio: 'inherit', cwd: path_1.resolve(root, relativePath) });
./package/lib/modules/setup/setupTooling.js:    child_process_1.execSync(`${utils_1.yarnPath} add -D ${depList}`, {
./package/lib/modules/release/utils.js:        output = child_process_es6_promise_1.execSync(cmd, { stdio: hideOutput ? 'pipe' : 'inherit', cwd: root });
./package/lib/modules/release/utils.js:        child_process_es6_promise_1.execSync('git --version');
./package/lib/modules/release/utils.js:        child_process_es6_promise_1.execSync('git rev-parse --git-dir');
```

etc.
