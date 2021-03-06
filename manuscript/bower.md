# Bower

Bower is the package manager for frontend components. If instead of separately
installing bootstrap and jquery for your frontend, user bower, and updates will
be a `bower update` away.

Find more [here](https://bower.io/)

## Bower CLI

```bash
# Initialize bower
$ bower init

# Install
$ bower install # All dependencies and devDependencies listed in bower.json
$ bower install --production # without devDependencies

# Search package in repostory
$ bower search jquery

# Install
$ bower install jquery # Install the registered package
$ bower install jquery --save # And save it in bower.json
$ bower install jquery --save-dev # And save it in bower.json devDependencies


# Other ways to install packages
$ bower install desandro/masonry # GitHub shorthand
$ bower install git://github.com/user/package.git # Git endpoint
$ bower install http://example.com/script.js # URL

# Update
$ bower update # update all installed packages
$ bower update --save # and update bower.json dependencies
$ bower update --save-dev # and update bower.json devDependencies

# Authenticate with Github
$bower login

# Register a package on bower
$ bower register mypackage git://github.com/myuser/mypackage.git

```

## Bowerrc

A configuration file for your bower -- optional

```json
{
  "cwd": "~/.my-project",
  "directory": "bower_components",
  "registry": "https://bower.herokuapp.com",
  "shorthand-resolver": "git://github.com//.git",
  "proxy": "http://proxy.local",
  "https-proxy": "http://proxy.local",
  "ca": "/var/certificate.pem",
  "color": true,
  "timeout": 60000,
  "save": true,
  "save-exact": true,
  "strict-ssl": true,
  "storage": {
    "packages" : "~/.bower/packages",
    "registry" : "~/.bower/registry",
    "links" : "~/.bower/links"
  },
  "interactive": true,
  "resolvers": [
    "mercurial-bower-resolver"
  ],
  "shallowCloneHosts": [
    "myGitHost.example.com"
  ],
  "scripts": {
    "preinstall": "",
    "postinstall": "",
    "preuninstall": ""
  },
  "ignoredDependencies": [
    "jquery"
  ]
}
```

## Bower.json

Specifications for your bower project. Adapted from the [specs](https://github.com/bower/spec/blob/master/json.md#name)

```js
{
  "name": "blue-leaf", // 50 chars max, no spaces or uppercase
  "description": "Physics-like animations for pretty particles", // max 140 chars
  "main": [ // entrypoint files, one per filetype
    "js/motion.js", // import all other js files into this
    "sass/motion.scss" // only one per filetype
  ],
  "dependencies": { // things this package depends on
    "get-size": "~1.2.2",
    "eventEmitter": "~4.2.11"
  },
  "devDependencies": { // things development depends on
    "qunit": "~1.16.0"
  },
  "moduleType": [ // The type of module defined in the `main` JavaScript file
    "amd",
    "globals",
    "node",
    "es6",
    "yui"
  ],
  "keywords": [
    "motion",
    "physics",
    "particles"
  ],
  "authors": [
    "Betty Beta <bbeta@example.com>"
  ],
  "license": "MIT",
  "ignore": [ // like gitignore for bower
    "**/.*",
    "node_modules",
    "bower_components",
    "test",
    "tests"
  ],
  "private": true // Bower will disallow accidentally publishing to registry.
}
```
