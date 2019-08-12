---
title: "What's up with Grant-DfsnAccess"
layout: post
date: 2019-08-12 17:15:00
lang: en
summary: "Short note about this Powershell cmdlet"
---
For our environment we use a selfservice portal (built in-house) where we are trying to seperate the actual code for performing an action from the front-end code. For our DFS infrastructure the most suitable solution is a PowerShell endpoint with purpose built functions. On of these is setting security groups on DFS links to allow Access Based Enumeration (ABE) to only show links the user actually has access to. For this I need to do a very ugly ‘breakout’ from Powershell and use the DfsUtil.exe.

```powershell
$Procs = Get-Process | Where {$_.Name -notlike "notepad*"}
```
The issue is however not completely isolated to Powershell since our old method -C# code- was producing the same results. So the deeper problem in my opinion lies within the .NET Framework.

Still it is a shame this has been known for a long time and Microsoft doesn’t seem to be working on a solution. I will be checking Windows Server 2016 TP5 shortly to find if this has been fixed

Please refer to [The Windows PowerShell cmdlet Grant-DfsnAccess does not change inheritance on DFS links](https://support.microsoft.com/en-us/kb/2938148) for the Microsft Knowledge Base article.
