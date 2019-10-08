# Netch Mode

An repository for storing Netch's mode files.

[简体中文](docs/README.zh-CN.md)

## TOC

1. [Usage](#usage)
2. [First line format](#first-line-format)
3. [Different mode types](#different-mode-types)
4. [Process mode example file](#process-mode-example-file)
5. [TUN/TAP blacklist proxy mode example file](#tuntap-blacklist-proxy-mode-example-file)
6. [TUN/TAP whitelist proxy mode example file](#tuntap-whitelist-proxy-mode-example-file)
7. [HTTP local proxy (with system proxy) mode example file](#http-local-proxy-with-system-proxy-mode-example-file)
8. [Socks5 local proxy (without system proxy) mode example file](#socks5-local-proxy-without-system-proxy-mode-example-file)
9. [Socks5 and HTTP local proxy (without system proxy) mode example file](#socks5-and-http-local-proxy-without-system-proxy-mode-example-file)

## Usage

All the mode files should be put under `mode` folder in the directory where `Netch.exe` is located.
 
## First line format

```Python
# Remark, Type(Its value is the Type mentioned in usage.md minus 1), IsBypassChina(1 for yes, 0 for no)
```

## Different mode types

- 0 for process mode.
- 1 for TUN/TAP blacklist proxy mode.
- 2 for TUN/TAP whitelist proxy mode.
- 3 for HTTP local proxy (with system proxy) mode.
- 4 for Socks5 local proxy (without system proxy) mode.
- 5 for Socks5 and HTTP local proxy (without system proxy) mode.

For mode 1 and mode 2, except for the first line format, other content is the same as the [SSTap-Rule](https://github.com/FQrabbit/SSTap-Rule). IsBypassChina feature depends on the [CNIP file](https://github.com/NetchX/Netch/blob/master/Netch/Resources/CNIP).

From mode 3 to mode 5, IsBypassChina feature depends on the [acl file](https://github.com/NetchX/Netch/blob/master/binaries/default.acl).

## Process mode example file

In the first line of this mode, only the Remark is valid.

```
# Remark
Process name 1(Which will be run through the proxy server.)
Process name 2
...
```

## TUN/TAP blacklist proxy mode example file

In this mode, the value of IsBypassChina is invalid.

```
# Remark, 1
Classless Inter-Domain Routing notation 1(The Network requests whose destination IP address is in this subnetwork will be forwarded to the proxy.)
Classless Inter-Domain Routing notation 2
...
```

## TUN/TAP whitelist proxy mode example file

```
# Remark, 2, IsBypassChina(1 for yes, 0 for no)
Classless Inter-Domain Routing notation 1(The Network requests whose destination IP address is in this subnetwork will not be forwarded to the proxy.)
Classless Inter-Domain Routing notation 2
...
```

## HTTP local proxy (with system proxy) mode example file

```
# Remark, 3, IsBypassChina(1 for yes, 0 for no)
(Currently only the first line is valid)
```

## Socks5 local proxy (without system proxy) mode example file

```
# Remark, 4, IsBypassChina(1 for yes, 0 for no)
(Currently only the first line is valid)
```

## Socks5 and HTTP local proxy (without system proxy) mode example file

```
# Remark, 5, IsBypassChina(1 for yes, 0 for no)
(Currently only the first line is valid)
```