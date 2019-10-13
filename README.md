# Netch Mode

A repository for storing Netch's mode files.

[简体中文](docs/README.zh-CN.md)（此版本内容更丰富）

## TOC

1. [Usage](#usage)
   - 1.1 [Add Proxy Servers](#add-proxy-servers)
   - 1.2 [Fast Create Mode](#fast-create-mode)
   - 1.3 [Scan](#scan)
   - 1.4 [Start](#start)
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

- Now Netch is under early development. Several changes may happen in the later releases. This guide for usage is just for your information.

### Add Proxy Servers

You can add it manually by filling in the input bars or importing URL from the clipboard. This demo uses the latter.

If your proxy protocol is currently not supported, you can manually add a socks5 server config to forward the network traffic to your proxy client's local socks5 server.

![](https://raw.githubusercontent.com/NetchX/Netch/master/docs/screenshots/Import_Servers_From_Clipboard.png)

If you found that your program visual is not as clear as the one in the screenshot, you can right-click Netch.exe - Properties - Compatibility - Change High DPI Settings - Override High DPI scaling behavior - System (Enhanced).

### Fast Create Mode

If your game name is on the mode list, you can use it directly by choosing it. All the mode files is under `./mode/` folder. You can use Notepad to open, modify or combine them.

![](https://raw.githubusercontent.com/NetchX/Netch/master/docs/screenshots/Fast_Create_Mode.png)

The green number in the right corner of the server bar is the ping number. It may not be accurate since it is just the delay between you and the proxy server not the game server.

If your game name isn't on the list, you can try next step to manually create it.

Then click the Fast Create Mode on the menu.

### Scan

Click Scan in the pop-up window.

![](https://raw.githubusercontent.com/NetchX/Netch/master/docs/screenshots/Scan.png)

Browse the installation path of the game which you want to accelerate. Depends on the game, you may need to scan different paths. Reference [eaglemoe's blog](https://www.eaglemoe.com/archives/142).

>4. Browse the GTA5 installation path. Click OK. Program will auto-scan and add all the exe files in the folder.
>5. Click the scan twice. Browse the socialclub installation path(normally in `C:\Program Files\Rockstar Games\Social Club`). Then Click OK and Save.
>
>Note: Don't forget to add the SNS part of the game at the same time. For example, adding socialclub when adding GTA. Adding Uplay when adding Rainbow Six Siege.

This demo takes Warthunder as the example. Since Warthunder can launch without Steam, just add its installation path is OK.

![](https://raw.githubusercontent.com/NetchX/Netch/master/docs/screenshots/Browse_For_Folder_en.png)

It may take a few seconds to scan. Remember to fill in the Remark bar. If you need to add a single exe file, you can enter it in the edit bar to the left of the Add button.

After that, click the Save button.

![](https://raw.githubusercontent.com/NetchX/Netch/master/docs/screenshots/Save_the_mode.png)

### Start

Make sure the contents in the Server bar and the Mode bar are exactly what you need. Next click Start.

![](https://raw.githubusercontent.com/NetchX/Netch/master/docs/screenshots/Start.png)

After starting, you can launch the game by itself or use the launcher. Then the game's network traffic is in the proxy tunnel.

If you start the game before starting the Netch, restarting the game is recommended.

If you need the launcher's network traffic forwarded to the Netch, follow the previous method to scan the installation path of the launcher like Steam or Uplay.

## First line format

Below is the mode files first line format.

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
