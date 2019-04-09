---
title: "Golang Sub Tests"
date: 2019-05-10T22:53:52-04:00
draft: false
description: "t.Run() is a great way to improve table-driven tests"
tags: [golang,go,linux,windows,test]
---

t.Run() is a great way to improve table-driven tests and give them names:

```
func TestFunc(t *testing.T) {
    tests := map[string]struct {
        input   string
        input2  string
        want    string
    }{ 
        "simple": {input: "abc", input2: "#", want: "result"}, 
        "wrong":  {input: "def", input2: "$", want: "ok"},
        "no":     {input: "abc", input2: "^", want: "not-ok"},
        "yes":    {input: "xyz", input2: "&", want: "please"},
    }

    for name, tst := range tests {
        t.Run(name, func(t *testing.T) {
            got := funcToTest(tst.input, tc.input2)
            if tc.want != got) {
                t.Fatalf("%s: expected: %v, got: %#v", name, tc.want, got)
            }
        })
    }
}
```