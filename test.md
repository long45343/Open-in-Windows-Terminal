# 直接打开

## 添加到注册表

将下面命令保存为 `reg`格式 文件：`Add_Open_in_Windows_Terminal.reg`

```bash
Windows Registry Editor Version 5.00

; Add_Open_in_Windows_Terminal.reg
; Created by: zzjtnb
; Created on: Jul 3, 2021
; Updated on: Jul 3, 2021
; Tutorial: https://zzjtnb.com/blog/details/yjdkopeninwindowsterminalgly

;文件目录

[HKEY_CLASSES_ROOT\Directory\shell\OpenWTHereAsAdmin]
"MUIVerb"="Open in Windows Terminal(管理员)"
"Icon"="C:\\Users\\Administrator\\Pictures\\ico\\wt.ico"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\shell\OpenWTHereAsAdmin\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-d','\"\"\"%V\"\"\"')\""


;桌面背景
[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenWTHereAsAdmin]
"MUIVerb"="Open in Windows Terminal(管理员)"
"Icon"="C:\\Users\\Administrator\\Pictures\\ico\\wt.ico"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenWTHereAsAdmin\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-d','\"\"\"%V\"\"\"')\""
```

## 卸载

类似上面的，执行下面注册表命令就可以了：
新建文件`Remove_Open_in_Windows_Terminal_Context.reg`

```bash
Windows Registry Editor Version 5.00

; Remove_Open_in_Windows_Terminal.reg
; Created by: zzjtnb
; Created on: Jul 3, 2021
; Tutorial: https://zzjtnb.com/blog/details/yjdkopeninwindowsterminalgly


[-HKEY_CLASSES_ROOT\Directory\shell\OpenWTHereAsAdmin]

[-HKEY_CLASSES_ROOT\Directory\Background\shell\OpenWTHereAsAdmin]
```

# 上下文格式

## 添加到注册表

将下面命令保存为 `reg`格式 文件：`Add_Open_in_Windows_Terminal_Context.reg`

```bash
Windows Registry Editor Version 5.00

; Add_Open_in_Windows_Terminal_Context.reg
; Created by: zzjtnb
; Created on: Jul 3, 2021
; Updated on: Jul 3, 2021
; Tutorial: https://zzjtnb.com/blog/details/yjdkopeninwindowsterminalgly

;文件目录
[HKEY_CLASSES_ROOT\Directory\shell\OpenWTHereAsAdminContext]
"HasLUAShield"=""
"MUIVerb"="Open in Windows Terminal"
"Icon"="C:\\Users\\Administrator\\Pictures\\ico\\wt.ico"
"Extended"=-
"SubCommands"=""

[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\001flyout]
"MUIVerb"="默认终端(管理员)"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\001flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-d','\"\"\"%V\"\"\"')\""

;命令提示符(管理员)
[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\002flyout]
"MUIVerb"="命令提示符(管理员)"
"Icon"="imageres.dll,-5323"

[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\002flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"命令提示符\"\"\"','-d','\"\"\"%V\"\"\"')\""

;PowerShell(管理员)
[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\003flyout]
"MUIVerb"="PowerShell(管理员)"
"HasLUAShield"=""
"Icon"="pwsh.exe"

[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\003flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"PowerShell\"\"\"','-d','\"\"\"%1\"\"\"')\""

;Windows PowerShell(管理员)
[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\004flyout]
"MUIVerb"="Windows PowerShell(管理员)"
"HasLUAShield"=""
"Icon"="powershell.exe"

[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\004flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"Windows PowerShell\"\"\"','-d','\"\"\"%1\"\"\"')\""

;Ubuntu(管理员)
[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\005flyout]
"MUIVerb"="Ubuntu(管理员)"
"HasLUAShield"=""
"Icon"="wsl.exe"

[HKEY_CLASSES_ROOT\Directory\Shell\OpenWTHereAsAdminContext\shell\005flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"Ubuntu\"\"\"','-d','\"\"\"%1\"\"\"')\""

;桌面背景

[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenWTHereAsAdminContext]
"HasLUAShield"=""
"MUIVerb"="Open in Windows Terminal"
"Icon"="C:\\Users\\Administrator\\Pictures\\ico\\wt.ico"
"Extended"=-
"SubCommands"=""

[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\001flyout]
"MUIVerb"="默认终端(管理员)"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\001flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-d','\"\"\"%V\"\"\"')\""

;命令提示符(管理员)
[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\002flyout]
"MUIVerb"="命令提示符(管理员)"
"Icon"="imageres.dll,-5323"

[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\002flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"命令提示符\"\"\"','-d','\"\"\"%V\"\"\"')\""

;PowerShell(管理员)
[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\003flyout]
"MUIVerb"="PowerShell(管理员)"
"HasLUAShield"=""
"Icon"="pwsh.exe"

[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\003flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"PowerShell\"\"\"','-d','\"\"\"%V\"\"\"')\""

;Windows PowerShell(管理员)
[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\004flyout]
"MUIVerb"="Windows PowerShell(管理员)"
"HasLUAShield"=""
"Icon"="powershell.exe"

[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\004flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"Windows PowerShell\"\"\"','-d','\"\"\"%V\"\"\"')\""

;Ubuntu(管理员)
[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\005flyout]
"MUIVerb"="Ubuntu(管理员)"
"HasLUAShield"=""
"Icon"="wsl.exe"

[HKEY_CLASSES_ROOT\Directory\Background\Shell\OpenWTHereAsAdminContext\shell\005flyout\command]
@="powershell.exe -WindowStyle Hidden \"Start-Process -Verb RunAs cmd.exe -ArgumentList @('/c','start wt.exe','-p','\"\"\"Ubuntu\"\"\"','-d','\"\"\"%V\"\"\"')\""
```

注意文件字符格式为 `utf-8 with bom`或着`GBK`或`GBK(132)`
然后双击执行就可以了。

## 卸载

类似上面的，执行下面注册表命令就可以了：
新建文件`Remove_Open_in_Windows_Terminal_Context.reg`

```bash
Windows Registry Editor Version 5.00

; Remove_Open_in_Windows_Terminal_Context.reg
; Created by: zzjtnb
; Created on: Jul 3, 2021
; Tutorial: https://zzjtnb.com/blog/details/yjdkopeninwindowsterminalgly


[-HKEY_CLASSES_ROOT\Directory\shell\OpenWTHereAsAdminContext]

[-HKEY_CLASSES_ROOT\Directory\Background\shell\OpenWTHereAsAdminContext]
```
