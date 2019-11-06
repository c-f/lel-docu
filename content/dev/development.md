---
title: "Development Guide"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 2
summary: Information and guides to set up the development environment
---

Thanks for looking by - maybe this is helpful for you. If not the source code is available at [Github](https://github.com/c-f/lel)

## Contributing

If you want to contribute: feel free to do so :)

## Backend

IT's go :D nothing really to explain, install dependencies and build LEL.

```
lel@srv:~/lel$ go get
lel@srv:~/lel$ goxc
lel@srv:~/lel/cmd$ go build . -t LEL
```

For running configuration you can use dev.yml

```bash
lel@srv:~/lel/cmd$ ./LEL -debug -docu stuff
```

## Frontend

Since I'm no frontend expert i'd love some tips :D

Start LEL and the npm serve

```bash

lel@srv:~/lel/cmd$ go run *.go -d
lel@srv:~/lel/static$ npm install <stuff>
lel@srv:~/lel/static$ npm run serve
```

Then go to [http://127.0.0.1:8080/dev.html](http://127.0.0.1:8080/dev.html) to see the react component.

The go server can be started with `-debug` to enable support to other ports.

## Errors & Pitfalls

if compiling isn't working increase the inodes: [Answer](https://webpack.js.org/configuration/watch/#not-enough-watchers)

```
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```
