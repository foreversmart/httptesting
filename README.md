# httptesting

[![Build Status](https://travis-ci.org/dolab/httptesting.svg?branch=master&style=flat)](https://travis-ci.org/dolab/httptesting)

HTTP testing client of golang.

## Installation

```bash
$ go get github.com/dolab/httptesting
```

## Getting Started

```go
package main

import (
    "net/http"
    "testing"

    "github.com/dolab/httptesting"
)

func Test_Client(t *testing.T) {
    host := "https://example.com"
    test := httptesting.New(host, true)

    test.Get("/")
    test.AssertOK()
    test.AssertNotEmpty()
}

func Test_ClientWithCustomRequest(t *testing.T) {
    r, _ := http.NewRequest("HEAD", "https://example.com", nil)
    r.Header.Add("X-Custom-Header", "custom-header")

    test := httptesting.New("", true)

    test.NewRequest(r)
    test.AssertOK()
    test.AssertEmpty()
}
```

## Author

[Spring MC](https://twitter.com/mcspring)

## LICENSE

```
The MIT License (MIT)

Copyright (c) 2016

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
