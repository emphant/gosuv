# gosuv
[![Build Status](https://travis-ci.org/codeskyblue/gosuv.svg)](https://travis-ci.org/codeskyblue/gosuv)

## Program not implement
Process managerment writtern by golang, inspired by python-supervisor

Features

* [x] Realtime log view
* [x] Web control page
* [ ] Github webhook
* [ ] 中文文档

## Requirements
Go version at least `1.6+`

## Installation
Binary can be download from <https://dl.equinox.io/shengxiang/gosuv/stable>

Or if you have go enviroment, you can also build from source.

```sh
go get -d github.com/codeskyblue/gosuv
cd $GOPATH/src/github.com/codeskyblue/gosuv
go build
```

If you want to build a standalone binary, run the following command.

```sh
go get github.com/elazarl/go-bindata-assetfs/...
go-bindata-assetfs -tags bindata res/...
go build -tags bindata
```

## Usage
Start server in the background

```sh
gosuv start-server
```

Show server status

```sh
$ gosuv status
Server is running
```

## Configuration
Default config file stored in directory `$HOME/.gosuv/`

## Design
HTTP is follow the RESTFul guide.

Get or Update program

`<GET|PUT> /api/programs/:name`

Add new program

`POST /api/programs`

Del program

`DELETE /api/programs/:name`

## State
Only 4 states. [ref](http://supervisord.org/subprocess.html#process-states)

![states](docs/states.png)

# Plugin Design (todo)
Current plugins:

- [tailf](https://github.com/codeskyblue/gosuv-tailf)

All command plugin will store in `$HOME/.gosuv/cmdplugin`, gosuv will treat this plugin as a subcommand.

for example:

	$HOME/.gosuv/cmdplugin/ --.
		|- showpid/
			|- run

There is a directory `showpid`

When run `gosuv showpid`, file `run` will be called.


## Use libs
* <https://github.com/ahmetalpbalkan/govvv>

## LICENSE
[MIT](LICENSE)
