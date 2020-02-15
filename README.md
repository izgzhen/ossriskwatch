# OSS Risk Watch

A list of new & interesting OSS code.

## npm

### Potential vulnerabilities

e.g. passes variable or high-privilege commands to `execSync` here.

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

### Broken code

https://unpkg.com/event-stream@0.8.0/index.js

```

<<<<<<< index.js

//a do nothing stream that just passes through

es.through = function () {
  var s = new Stream()
  s.readable = true
  s.writeable = true
  s.write = function (data) {
    this.emit('data', data)
    return true
  }
  s.end = function (data) {
    if(data)
      this.write(data)
    this.emit('end')
    this.writable = false
  }
  return s
}


||||||| node_modules/event-stream/index.js
=======
// through
//
// a stream that does nothing but re-emit the input.
// useful for aggregating a series of changing but not ending streams into one stream)

es.through = function () {
  var stream = new Stream()
  stream.readable = stream.writable = true
  
  stream.write = function (data) {
    stream.emit('data', data)
  }
  stream.end = function (data) {
    if(data)
      stream.emit('data',data)
    stream.emit('end')
  }
  return stream
}


>>>>>>> ../snob/node_modules/event-stream/index.js
```

```
results/hookagent@0.7.2-execSync.txt_dot/package/server.js.dot
	"[const]su - -c env"->"[call][const]execSync" [type=DATAFLOW,];


results/homebridge-config-ui-x@4.10.0-execSync.txt_dot/package/dist/self-check.js.dot
	"[const]sudo -E -n npm rebuild node-pty-prebuilt-multiarch --unsafe-perm"->"[call][const]execSync" [type=DATAFLOW,];
```
