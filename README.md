# JSON Resume Registry Server

[![Join the chat at https://gitter.im/jsonresume/public](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/jsonresume/public?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://travis-ci.org/jsonresume/registry-server.svg?branch=master)](https://travis-ci.org/jsonresume/registry-server) [![Dependency Status](https://david-dm.org/jsonresume/registry-server.svg)](https://david-dm.org/jsonresume/registry-server) [![devDependency Status](https://david-dm.org/jsonresume/registry-server/dev-status.svg)](https://david-dm.org/jsonresume/registry-server#info=devDependencies)
﻿[![Issue Stats](https://www.issuestats.com/github/jsonresume/registry-server/badge/pr?style=flat)](https://www.issuestats.com/github/jsonresume/registry-server) [![Issue Stats](https://www.issuestats.com/github/jsonresume/registry-server/badge/issue?style=flat)](https://www.issuestats.com/github/jsonresume/registry-server)



## Installation

Requirements: MongoDB, Redis

1. Clone the repository
1. `npm install`
1. `git submodule update --init --recursive --depth 1`
1. `mongo 127.0.0.1:27017/jsonresume --eval "db.resumes.insert({})"`
1. `POSTMARK_API_KEY=1234567889 MONGOHQ_URL=mongodb://127.0.0.1:27017/jsonresume node server.js`

*Alternatively:*

Requirements: Vagrant, VirtualBox(or other providers)

1. Clone the repository
1. `vagrant up`
1. `vagrant ssh`
1. `POSTMARK_API_KEY=1234567889 MONGOHQ_URL=mongodb://127.0.0.1:27017/jsonresume node server.js`

### Install & run with docker-compose

Docker-compose allows isolation of each component of the solution: mongodb, redis, theme-manager and registry-server.

### Limitations

For now, registry-server is not starting automatically. I should be started manually after its dependencies (mongodb and redis) are up.

Theme-manager is not yet included in docker-compose.

#### Pre-requisites

It is assumed that registry-server are installed in separate folders, side-by-side.

#### Install procedure

1. run the following commands:
    ```
    cd ~/proj/registry-server
    sudo docker-compose up -d
    ```

This will start mongodb and redis services.

1. spin up the registry-server container:

    `sudo docker-compose run registry-server bash`

1. and then, start the registry-server service:

    `node server.js`

1. to access the registry-server, we need to discover its IP running the following command:

    `sudo docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(sudo docker ps -aq)`

1. to access the registry-server through the browser, go to the following address:

`http://<ip registry-server>:5000`

## Testing

To run the tests, simply run:

    npm test

## Documentation
For additional documentation please see the [Wiki page](https://github.com/jsonresume/resume-docs/wiki/Registry-Server).

## License

Available under [the MIT license](https://mths.be/mit).

