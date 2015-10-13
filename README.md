Mono (C#) and bash Docker image
======================
Docker image with alpine as base, including mono and bash

Shamelessly stolen from https://github.com/frol/docker-alpine-mono
Added bash and running of mozroots (for TLS/SSL support in mono)

This image is based on Alpine Linux image, which is only a 5MB image, and contains
[Mono](http://www.mono-project.com/).

WARNING: This mono was compiled for Arch Linux and is ported to Alpine via
[glibc hack](https://github.com/gliderlabs/docker-alpine/issues/11)! Ideally,
Mono package should be added to Alpine repo, but I don't have much time now.


Usage Example
-------------

```bash
$ echo -e 'using System; class MainClass { public static void Main (string[] args) { Console.WriteLine ("Hello World"); } }' > qq.mono
$ docker run --rm -v `pwd`:/tmp frolvlad/alpine-mono sh -c 'mcs -out:/tmp/qq.exe /tmp/qq.mono && mono /tmp/qq.exe'
```

Once you have run these commands you will have `qq.exe` mono-executable in your
current directory, and you will get printed 'Hello World' from Mono!
