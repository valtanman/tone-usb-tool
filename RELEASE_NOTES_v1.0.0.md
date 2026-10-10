# TONE USB Tool v1.0.0

**English**

First public release.

- **All-in-one**: full erase → write ISO → SHA-256 verification → safe eject, after one confirmation
- Write an ISO with read-back SHA-256 verification
- Forced wipe of a USB drive (quick or full), even while it is mounted
- Optional ISO pre-check with `.sha256` / `SHA256SUMS`
- Never touches the running system's disk or the disk holding the ISO; refuses if the drive was swapped after you chose it
- Writes only to real block devices (never creates a plain file if the device node vanishes)
- UI in **English and Japanese** (auto-detected); add more languages with a `.lang` file (see README)
- Always shows a result dialog; log at `~/.cache/tone-os/usb-last.log`

**Install**: `sudo bash install-tone-usb-tool.sh` — **Verify**: `sha256sum -c SHA256SUMS`

⚠ This tool permanently erases the selected drive. Use at your own risk (MIT License, no warranty).

**日本語**

最初の公開版です。

- **全部入り**: 完全消去 → ISO書き込み → SHA-256検証 → 安全な取り外しを、確認1回で連続実行
- ISOの書き込みと、読み戻しによるSHA-256検証
- 使用中でも外して消せる、USBの強制真っ白(かんたん/完全)
- `.sha256` / `SHA256SUMS` があれば、書く前にISOを照合
- 動いているシステムのディスクとISOの入ったディスクには触れません。選んだ後に入れ替わったら拒否します
- 書き込みは本物のブロックデバイスだけ(デバイスが消えても普通のファイルは作りません)
- 表示は**日本語と英語**(自動判定)。`.lang` ファイルで言語を追加できます(READMEを参照)
- 結果は必ずダイアログで表示し、記録は `~/.cache/tone-os/usb-last.log` に残ります

**インスコ**: `sudo bash install-tone-usb-tool.sh` — **確認**: `sha256sum -c SHA256SUMS`

⚠ 選んだドライブのデータは完全に消えます。自己責任でお使いください(MITライセンス、無保証)。
