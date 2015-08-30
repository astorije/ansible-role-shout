[![Build Status](https://travis-ci.org/astorije/ansible-role-shout.svg?branch=master)](https://travis-ci.org/astorije/ansible-role-shout)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# ansible-role-shout

Ansible role to install Shout, a self-hosted web IRC client (http://shout-irc.com/).

What this role does:

- Installs [NodeSource Node.js 0.12](https://nodesource.com/blog/nodejs-v012-iojs-and-the-nodesource-linux-repositories)
- Installs [Shout 0.51.1](https://github.com/erming/shout/blob/master/CHANGELOG.md#0511--2015-04-29)
- Configures Shout [as a private server](http://shout-irc.com/docs/server/configuration.html#public) to enable user login
- Configures users as defined in your playbook variables
- Starts Shout server as a [Supervisor](http://supervisord.org/) program

Note that this playbook will also install [esprima](https://www.npmjs.com/package/esprima) and [jsonlint](https://www.npmjs.com/package/jsonlint) npm packages to check syntax of configuration files.

## Role variables

Users are defined by a list of the following format:

```yaml
shout_users:
  - user: jeremie
    hashed_password: $2a$04$wNuWT4t3YmzkVTvBT6OFYepxHqg5c.GeFHCwtq1lu3FAT5/WhURHe
  - ...
```

Passwords are hashed using [`bcrypt`](https://en.wikipedia.org/wiki/Bcrypt). To generate a password using the [bcryptjs](https://www.npmjs.com/package/bcryptjs) npm package, run the following commands:

```bash
npm install bcryptjs
 node node_modules/bcryptjs/bin/bcrypt myPassword
```

(Note that the `bcrypt` command is prefixed with a whitespace to [not be saved in your `bash` history](http://askubuntu.com/a/15929/166928), if configured accordingly).

**Warning:** At the moment, user configuration files are only created if they do not exist, so changing passwords does not get reflected when provisioning.

## Example playbook

TODO
