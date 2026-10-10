# Security Policy / セキュリティ方針

## Reporting a vulnerability / 脆弱性の報告

Please **do not open a public issue** for security problems.
Use GitHub's **"Report a vulnerability"** button on the *Security* tab of this repository (private vulnerability reporting).
If that button is not available, open an issue that says only "security contact requested" (no details), and the maintainer will reach out.

セキュリティ上の問題は、**公開のIssueに書かないでください**。
このリポジトリの *Security* タブにある **「Report a vulnerability」** から、非公開で報告してください。
ボタンが無い場合は、詳細を書かずに「security contact requested」とだけ書いたIssueを立ててください。連絡します。

## Scope / 対象

This tool runs a privileged helper (`usb-root`, through `pkexec`) that erases and writes disks. Reports about the following are especially welcome:

- Any way to make it erase or write the **running system's disk** or the disk holding the ISO
- Any way to make it write to a **different device than the one the user confirmed**
- Privilege escalation through arguments, file names, or language files
- Anything that makes it report success when the data was not actually written or erased

管理者権限で動く `usb-root`(`pkexec` 経由)が、ディスクの消去・書き込みを行います。次のような報告は特に歓迎します。

- 動いているシステムのディスク、またはISOが入っているディスクを、消したり書いたりできてしまう方法
- ユーザーが確認したものとは**別のデバイス**に書き込ませる方法
- 引数・ファイル名・言語ファイルを使った権限の昇格
- 実際には書き込み・消去できていないのに、成功と表示させる方法

## Supported versions / 対象の版

Only the latest release is supported. / 最新のリリースのみ対象です。

## Verifying downloads / 配布物の確認

```bash
sha256sum -c SHA256SUMS
```
