# 2024-18-03 - PowerShell - Show-MarkDown 

Today I learned that these PowerShell commands for Markdown are built in (since v7 I believe):

- `ConvertFrom-Markdown`
- `Show-Markdown`

```pwsh
$markdown | Show-Markdown
$markdown | Show-Markdown -UseBrowser
```
Could be useful.
Although, I'll still likely make use of [glow](https://github.com/charmbracelet/glow) in the terminal.
