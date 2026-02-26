## 🪟 Launch Ryujinx Without Console Window - VBS Script Method

**Step 1:** Create a new text file in your Ryujinx folder

**Step 2:** Paste this code:
```vbs
Set WshShell = CreateObject("WScript.Shell")
WshShell.Run chr(34) & "Ryujinx.exe" & Chr(34), 0
Set WshShell = Nothing
```

**Step 3:** Save it as `Ryujinx_NoConsole.vbs` (make sure it's `.vbs` not `.vbs.txt`)

**Step 4:** Double-click the VBS file to launch Ryujinx - no CMD window will appear

**Step 5 (Optional):** Create a shortcut with the Ryujinx icon:
- Right-click on `Ryujinx_NoConsole.vbs`
- Select "Create shortcut"
- Right-click the new shortcut → Properties
- Click "Change Icon"
- Click "Browse" and navigate to `Ryujinx.exe`
- Select the Ryujinx icon and click OK
- Move the shortcut to your Desktop or pin it to your taskbar/start menu
