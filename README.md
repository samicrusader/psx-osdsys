# PS2 Browser (OSD-SYS/HDD-OSD) on PSX DESR

<https://youtu.be/9riVUC7kSD4>

Original files come from <https://obscuregamers.com/threads/psx-desr-7000-dual-boot-xmb-and-hdd-osd.1354/post-19054.html>, repacked on not-MediaFire.

## Install

- Copy contents of [__system](__system) to `hdd0:/__system` in wLaunchELF
- Copy [osdsys.elf](osdsys.elf) to `mass:`/`mc0:`/`hdd0:/_common` and run

## Loading from XMB

- Create a 128MB (I wish there were smaller partitions...) partition named `PP.BIEXEC-SYSTEM` using wLaunchELF HDDManager
- Copy contents of [xmbload/PP.BIEXEC-SYSTEM](xmbload/PP.BIEXEC-SYSTEM) to `hdd0:/PP.BIEXEC-SYSTEM`

### wLaunchELF_ISR_HDD method (requires FAT32-formatted thumb drive)

- Create file path in root of flash drive named `\__Headers\PP.BIEXEC-SYSTEM`
- Copy [icon.sys](xmbload/icon.sys), [list.ico](xmbload/list.ico), [system.cnf](xmbload/system.cnf) from [xmbload](xmbload) folder to flash drive folder `\__Headers\PP.BIEXEC-SYSTEM\`
- Download latest [wLaunchELF_ISR_HDD](https://github.com/israpps/wLaunchELF_ISR_HDD) build `ULE_ISR_HDD.ELF`: <https://github.com/israpps/wLaunchELF_ISR_HDD/releases/tag/latest> and run on console
- Go into `MISC`/`HddManager`, hover your `PP.BIEXEC-SYSTEM` partition, press R1, then go to `Inject` and let it go.
- Shut PSX off and then turn it back on and go to games section then run "PS2 Browser"

### `hdl_svr` method (requires network)
- Create `mc?:/SYS-CONF/IPCONFIG.DAT` with
```
<ipv4 address> <subnet mask> <default gateway>
# EXTRACNF = mc0:extra.cnf;
```
- Download hdl_dump <https://github.com/ps2homebrew/hdl-dump/releases/download/v47/hdl_dumx_rev47.zip> and extract `hdl_svr_093.elf` to `mass:`/`mc0:`/`hdd0:/_common` and run on console
- Extract `hdl_dump.exe` to <xmbload> folder and run `hdl_dump inject_header <ipv4 address> PP.BIEXEC-SYSTEM`
- Run `hdl_dump poweroff <ipv4 address>`
- Turn PSX on and go to games section then run "PS2 Browser"