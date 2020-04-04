# lunar

[![GoDoc](https://godoc.org/github.com/hyperjiang/lunar?status.svg)](https://godoc.org/github.com/hyperjiang/lunar)
[![Build Status](https://travis-ci.org/hyperjiang/lunar.svg?branch=master)](https://travis-ci.org/hyperjiang/lunar)
[![](https://goreportcard.com/badge/github.com/hyperjiang/lunar)](https://goreportcard.com/report/github.com/hyperjiang/lunar)
[![codecov](https://codecov.io/gh/hyperjiang/lunar/branch/master/graph/badge.svg)](https://codecov.io/gh/hyperjiang/lunar)
[![Release](https://img.shields.io/github/release/hyperjiang/lunar.svg)](https://github.com/hyperjiang/lunar/releases)

Probably the most elegant ctrip apollo client in golang. This library has no third-party dependency.

Ctrip Apollo: https://github.com/ctripcorp/apollo

Default settings of `lunar`:

- default namespace is `application`
- default server is `localhost:8080`
- default http client timeout is `90s`

## Usage

```
import "github.com/hyperjiang/lunar"

key := "foo"

app := lunar.New("myAppID", lunar.WithServer("localhost:8080"))

// get value of key in default namespace
app.GetValue(key)

// get value of key in namespace ns
app.GetValueInNamespace(key, "ns")

// get all the items in default namespace
app.GetItems()

// get all the items in namespace ns
app.GetItemsInNamespace("ns")

// get the content of ns namespace, if the format of ns is properties then will return json string
app.GetContent("ns")

// watch changes
app.Watch()
```

## Logging

`lunar` does not write logs by default, if you want to see logs for debugging, you can replace it with any logger which implements `lunar.Logger` interface.

`lunar` also provide a simple logger `lunar.Printf` which writes to stdout:

```
app := lunar.New("myAppID", lunar.WithServer("localhost:8080"), lunar.WithLogger(lunar.Printf))
```
