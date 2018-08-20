---
title: windows10微软输入法变纯小鹤双拼输入法
date: 2018-08-20 12:08:39
tags:
---
原文地址： http://www.flypy.com/bbs/forum.php?mod=viewthread&tid=166

使用方法： 
1.复制下示文本内容，打开你的文本编辑器（#记事本notepad或其他++），粘贴文本内容并保存在任意位置（不影响使用） 
2.变动该文本后缀，改为reg，让文件系统可以正确识别文件为注册表文件 
3.直接双击文件导入注册表，确定提示框中的安全提示，你的windows10微软输入法就默认为小鹤双拼了

```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\InputMethod\Settings\CHS]
"LangBar Force On"=dword:00000000
"Enable Double Pinyin"=dword:00000001
"EmoticonTipTriggerCount"=dword:00000001
"HapLastDownloadTime"=hex(b):eb,69,29,59,00,00,00,00
"UserDefinedDoublePinyinScheme0"="FlyPY*2*^*iuvdjhcwfg xmlnpbksqszxkrltvyovt"
"DoublePinyinScheme"=dword:0000000a
"UDLLastUpdatedTime"="2017-05-27 22:01:40"
"UDLCount"=dword:0000018b
"UDLVisibleCount"=dword:0000018b
```
原理：windows10内置微软拼音输入法双拼配置保存在注册表`[HKEY_CURRENT_USER\Software\Microsoft\InputMethod\Settings\CHS]`位置。