# msfs_simconnect_go

Originally forked from https://github.com/lian/msfs2020-go

## Intro

Accessing the MSFS simconnect API from a separate (Windows) executable, using the Go language.

The idea is to connect to the MSFS 'sim' world via two mechanisms:

1. Using a loop in the Go program which peridically 'requests' data from MSFS (this 'polling' is the method originally
forked from msfs2020-go).

2. Registering a 'callback' so the *sim* can send data to the Go program when appropriate in the MSFS update cycle
(this is a much more sensible way to communicate with MSFS).

The Go programming language (aka Golang) provides as standard HTTP/web support including websockets, so this Go/simconnect support
can communicate with other programs on remote machines via a websocket if required.

## Installation

Install Golang
Git Clone https://github.com/ijl20/msfs_simconnect_go
```
cd msfs_simconnect_go
go build -ldflags "-s -w" ./vfrmap
./vfrmap.exe
```

cross-compiles from macos/linux, no other dependencies required. produces a single binary with no other files or configuration required.

## Status

[msfs_simconnect_go/simconnect](simconnect/) package currently only implements enough of the simconnect api for [examples](examples/) and [vfrmap](vfrmap).

## Releases and download

program zips releases are uploaded [here](https://github.com/ijl20/msfs_simconnect_go/releases)

## Examples

* [vfrmap](vfrmap/) local web-server that will allow you to view your location, and some information about your trajectory including airspeed and altitude.

* [examples/request_data](examples/request_data/) port of `MSFS-SDK/Samples/SimConnectSamples/RequestData/RequestData.cpp`

## Support notes

### Why does my virus-scanning software think this program is infected?

From official golang website https://golang.org/doc/faq#virus

"This is a common occurrence, especially on Windows machines, and is almost always a false positive.
Commercial virus scanning programs are often confused by the structure of Go binaries, which they don't
see as often as those compiled from other languages."
