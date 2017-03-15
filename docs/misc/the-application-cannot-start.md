---
title: "The application cannot start. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot start.
发生意外的错误，导致无法启动 Visual Studio。  在发生下列情况之一时将会出现该错误：  
  
-   集成开发环境 \(IDE\) 无法加载 Msxml3.dll。  
  
-   IDE 无法加载 Mso.dll。  
  
-   IDE 无法加载 DTE.olb。  
  
-   安装过程中未创建 Visual Studio 许可证密钥。  
  
-   启用了脚本拦截，不允许执行脚本代码。  
  
-   .NET Framework 的安装程序（Visual Studio 所需组件）无法生成 mscorlib.dll 的有效本机映像。  
  
-   你的计算机上出现 Klez 病毒。  
  
 使用以下步骤更正此错误。  
  
> [!WARNING]
>  这些解决方案中的某一些要求修改注册表项。  注册表编辑器使用不当可能导致严重问题，进而导致需要重新安装操作系统。  Microsoft 无法保证可以解决因注册表编辑器使用不当而造成的问题。  使用注册表编辑器的风险由用户自行承担。  
  
 IDE 无法加载 Msxml3.dll。  
 2001 年 7 月发布的 MSXML 4.0 技术预览版 Beta 版使计算机处于可能出现此问题的状态。  若要修复 Msxml3.dll 注册，请按照下列步骤进行操作：  
  
### 卸载 Msxml4.dll  
  
1.  从**“开始”**菜单上，选择**“运行”**。  
  
2.  在**“打开”**文本框中，键入 `regsvr32 /u c:\winnt\system32\msxml4.dll` 并单击**“确定”**。  
  
### 下载并安装 MSXML 的安全更新  
  
1.  从 [http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp) 下载计算机上 MSXML 版本的最新安全更新。  
  
2.  运行安全更新的 .exe。  
  
### 下载并应用更新的注册表值  
  
1.  从 [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe) 下载更新的注册表值。  
  
2.  双击 fixxml4.exe 并解压缩文件。  
  
3.  找到 Fixxml4.reg 并双击该文件，以更新注册表值。  
  
 IDE 无法加载 Mso.dll。  
 使用以下列表解决与 Mso.dll 有关的问题。  
  
### Microsoft Office  
  
-   卸载计算机上的任何 Microsoft Office XP Beta 版本。  
  
-   通过“添加\/删除程序”修复 Office XP。  
  
-   在注册表编辑器中，验证以下注册表项：  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 IDE 无法加载 DTE.olb。  
 更正此错误的步骤：  
  
### 注册 Dte.olb  
  
1.  从**“开始”**菜单上，选择**“运行”**。  
  
2.  在**“打开”**文本框中，键入 `regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB` 并单击**“确定”**。  
  
 安装过程中未创建 Visual Studio 许可证密钥。  
 如果 Visual Studio 的初始屏幕不包含已安装产品的列表，并且不包括有关安装本产品的人员的信息，则表示缺少许可证密钥。  同样，如果“添加\/删除程序”对话框中未列出“Visual Studio”，也表示缺少许可证密钥。  
  
 若要更正这一问题：  
  
### 为 Visual Studio 创建许可证密钥  
  
-   从计算机中完全删除 Visual Studio，然后重新安装该产品。  
  
 启用了脚本拦截，不允许执行脚本代码。  
 如果第三方应用程序启用了脚本拦截，IDE 将出现然后消失。  
  
-   若要更正此问题，请验证脚本拦截功能正常工作。  
  
 .NET Framework 的安装程序（Visual Studio 所需组件）无法生成 mscorlib.dll 的有效本机映像。  
 如果 Visual Studio 的初始屏幕短暂出现然后消失，则可能缺少 Mscorlib.dll 文件的有效本机映像。  该文件在 .NET Framework 安装过程中在 \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib 目录下创建。  
  
 更正此错误的步骤：  
  
### 创建有效的 Mscorlib.dll 文件  
  
1.  卸载并重新安装 .NET Framework。  
  
 你的计算机上出现 Klez 病毒。  
 如果计算机感染 Klez 病毒，可能会出现“该应用程序无法启动。”错误。  建议更新防病毒软件，然后扫描计算机中是否有病毒。