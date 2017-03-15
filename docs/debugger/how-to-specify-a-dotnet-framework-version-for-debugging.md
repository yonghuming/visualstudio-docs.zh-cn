---
title: "如何：指定用于调试的 .NET Framework 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, 指定要调试的版本"
  - "调试 [Visual Studio], 指定 .NET Framework 版本"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：指定用于调试的 .NET Framework 版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 调试器支持调试 Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的早期版本和当前版本。  如果您从 Visual Studio 启动应用程序，则调试器可以始终为正在进行调试的应用程序识别 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的正确版本。  如果应用程序已在运行并且您使用**“附加到”**，则调试器并不总是能标识 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的较早版本。  如果发生这种情况，您将收到一条错误消息，指出：  
  
 调试器对您的应用程序要使用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本进行了错误的假设。  
  
 在这些不常见的情况下，您可设置注册表项以指示调试器要使用的版本。  
  
### 指定用于调试的 .NET Framework 版本  
  
1.  在 Windows\\Microsoft.NET\\Framework 目录中查找您计算机上安装的 .NET Framework 的版本。  这些版本号类似于：  
  
     `V1.1.4322`  
  
     识别正确的版本号并记录下来。  
  
2.  启动**“注册表编辑器”**\(regedit\)。  
  
3.  在**“注册表编辑器”**中打开 HKEY\_LOCAL\_MACHINE 文件夹。  
  
4.  定位到：HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     如果该项不存在，请右击 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine，然后单击**“新建项”**。  将新项命名为 `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`。  
  
5.  定位到 {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} 后，在**“名称”**列中查找 CLRVersionForDebugging 项。  
  
    1.  如果该项不存在，请右击 {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}，然后单击**“新建字符串值”**。  然后右击该新建字符串值，单击**“重命名”**，并键入 `CLRVersionForDebugging`。  
  
6.  双击**“CLRVersionForDebugging”**。  
  
7.  在**“编辑字符串”**框中，在**“值”**框中键入 .NET Framework 版本号。  例如：V1.1.4322  
  
8.  单击**“确定”**。  
  
9. 关闭**“注册表编辑器”**。  
  
     如果开始调试时仍然收到错误消息，请验证是否已在注册表中正确输入了版本号。  还请验证您是否正在使用 Visual Studio 支持的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  调试器与 .NET Framework 当前版本及早期版本兼容，但可能与未来的版本不向前兼容。  
  
## 请参阅  
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)