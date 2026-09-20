# MagiskFrida

![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/ViRb3/magisk-frida/main.yml?branch=master)
![GitHub repo size](https://img.shields.io/github/repo-size/ViRb3/magisk-frida)
![GitHub downloads](https://img.shields.io/github/downloads/ViRb3/magisk-frida/total)

> [Frida](https://frida.re) is a dynamic instrumentation toolkit for developers, reverse-engineers, and security researchers

> [MagiskFrida](README.md) lets you run frida-server on boot with multiple root solutions

## Supported root solutions

[Magisk](https://github.com/topjohnwu/Magisk), [KernelSU](https://github.com/tiann/KernelSU) and [APatch](https://github.com/bmax121/APatch)

## Supported architectures

`arm64`, `arm`, `x86`, `x86_64`

## Instructions

Install `MagiskFrida.zip` from [the releases](https://github.com/ViRb3/magisk-frida/releases)

> :information_source: Do not use the Magisk modules repository, it is obsolete and no longer receives updates

## Custom port

frida-server listens on `127.0.0.1:27042` by default. To use a different port, write it to
`/data/adb/magisk-frida.port` and reboot:

```bash
echo 41337 > /data/adb/magisk-frida.port
```

Connect with `frida-ps -H 127.0.0.1:41337`, or keep `-U` working by forwarding on the host with
`adb forward tcp:27042 tcp:41337`.

Delete the file to return to the default. The file lives outside the module directory, so it
survives module updates. An invalid or out-of-range value is ignored and the default is used.

## How fast are frida-server updates?

Instant! This module is hooked up to the official Frida build process

## Issues?

Check out the [troubleshooting guide](TROUBLESHOOTING.md)

## Building yourself

```bash
uv sync
uv run python3 main.py
```

- Release ZIP will be under `/build`
- frida-server downloads will be under `/downloads`
