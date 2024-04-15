# PS2 Browser (OSD-SYS/HDD-OSD) on PSX DESR

<https://youtu.be/9riVUC7kSD4>

Original files come from <https://obscuregamers.com/threads/psx-desr-7000-dual-boot-xmb-and-hdd-osd.1354/post-19054.html>, repacked on not-MediaFire.

## Install

- Copy contents of [__system](__system) to `hdd0:/__system` in wLaunchELF
- Copy [osdsys.elf](osdsys.elf) to `mass:`/`mc0:`/`hdd0:/_common` and run

## Loading from XMB

- Create a 128MB (I wish there were smaller partitions...) partition named `PP.BIEXEC-SYSTEM..OSDSYS` using wLaunchELF HDDManager
- Copy contents of [xmbload/PP.BIEXEC-SYSTEM..OSDSYS](xmbload/PP.BIEXEC-SYSTEM..OSDSYS) to `hdd0:/PP.BIEXEC-SYSTEM..OSDSYS`
- Create `mc?:/SYS-CONF/IPCONFIG.DAT` with
```
<ipv4 address> <subnet mask> <default gateway>
# EXTRACNF = mc0:extra.cnf;
```
- Download hdl_dump <https://github.com/ps2homebrew/hdl-dump/releases/download/v47/hdl_dumx_rev47.zip> and extract `hdl_svr_093.elf` to `mass:`/`mc0:`/`hdd0:/_common` and run
- Extract `hdl_dump.exe` to <xmbload> folder and run `hdl_dump inject_header <ipv4 address> PP.BIEXEC-SYSTEM..OSDSYS`
- Run `hdl_dump poweroff <ipv4 address>`
- Turn PSX on and go to games section then run "PS2 Browser"