---
Title: windows
Category: default
Author: Kevin Loughead
Date: 2021-11-19
Tags:
---

- to check windows version -- `Winkey + r` then type `winver`

- [to fix windows 11 context menu](https://www.reddit.com/r/Windows11/comments/pu5aa3/howto_disable_new_context_menu_explorer_command/)

  ```bash
  # Disable new context menu:
  reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
  ```

  ```bash
  # Restore new context menu:
  reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f
  ```

  Use command to disable context menu, then restart explorer

  ```bash
  taskkill /F /IM explorer.exe & start explorer
  ```
