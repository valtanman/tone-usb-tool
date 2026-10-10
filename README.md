# TONE USB Tool

[日本語はこちら → README.ja.md](README.ja.md)

A GUI tool for Linux (KDE / GNOME) to **write an ISO to a USB drive** and to **forcibly wipe a USB drive**.
It is part of TONE OS, but works on its own on Ubuntu-based Linux. UI languages: **English and Japanese** (auto-detected), more can be added with a language file.

> ## ⚠ Read this first
> This tool **completely erases** the USB drive you select. **It cannot be undone.**
> Even if the drive is in use (mounted), it is forcibly detached and erased. Double-check the target.
> No warranty (MIT License). Back up anything important first.

## Features

| Feature | What it does |
|---|---|
| **All-in-one** | Full erase → write ISO → SHA-256 verification → safe eject (power off), in one go after a single confirmation |
| Write an ISO | Writes the ISO, then reads it back and compares SHA-256 |
| Wipe a USB drive (forced) | Detaches anything using the drive, then erases signatures, partition tables and the start/end of the disk. "Full erase" wipes the whole drive |
| ISO pre-check | If `<name>.iso.sha256` or `SHA256SUMS` sits next to the ISO, it is checked before writing |

## Safety

- The disk of the **running system** (boot disk / live medium) and the **disk holding the ISO** are never offered and are refused even in forced mode.
- If the **capacity or serial number changes** after you choose (drive swapped), it is refused.
- It writes only to **real block devices**. If the device node vanishes mid-way, it never creates or writes a plain file; it waits for the device to come back, or stops without writing.
- Internal (non-USB) disks can be chosen only when no USB drive is found, and only after you type the **full device name**.
- Every result is shown in a dialog, and logged to `~/.cache/tone-os/usb-last.log`.

## Install

```bash
sudo bash install-tone-usb-tool.sh
```

Start **TONE USB Tool** from the menu (you can also right-click an ISO and open it with the tool).

Uninstall:

```bash
sudo bash install-tone-usb-tool.sh --uninstall
```

Requires: `kdialog` or `zenity`, `pkexec` (polkit), `util-linux`, `gdisk` (the installer tries to install them).

## Languages

The UI language follows your locale (`LANG`). Japanese (`ja`) and English (`en`) are built in; anything else falls back to English.

To add a language (for example Arabic), copy `lang/en.lang` to `ar.lang`, translate the right-hand side of each `key=value` line, and put it in one of:

- `~/.config/tone-usb/lang/` (just for you)
- `/usr/local/share/tone-usb/lang/` (all users)

Rules: `\n` is a newline, `%1 %2 …` are replaced by values. Missing keys fall back to English. Language files are read **as data and never executed**, so a language file cannot run commands. The privileged helper (`usb-root`) never reads language files at all; it only emits message codes.

To force a language: put the code in `~/.config/tone-usb/language` (for example `echo ja > ~/.config/tone-usb/language`), or set `TONE_LANG` for one run (`TONE_LANG=ar tone-usb-flash`). Order of priority: `TONE_LANG` → that file → your locale.

## Files

- `install-tone-usb-tool.sh` – self-extracting installer (same content as `src/` and `lang/`)
- `src/tone-usb-flash` – front end (kdialog / zenity)
- `src/usb-root` – privileged helper (run through `pkexec`)
- `lang/*.lang` – language files
- `SHA256SUMS` – checksums of the distributed files (`sha256sum -c SHA256SUMS`)

## Troubleshooting

- Last result: `cat ~/.cache/tone-os/usb-last.log`
- `/dev/sdX` became a plain file (left over by an older version): `sudo rm -f /dev/sdX /dev/sdX[0-9]*`, then re-plug the drive
- "Still read-only": check the drive's write-protect switch, and try another port (USB 2.0 recommended)

## License

MIT (see `LICENSE`). Copyright (c) 2026 TONE (Seiji Okamoto / valtanman).
