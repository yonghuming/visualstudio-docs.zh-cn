---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. | Microsoft Docs"
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
  - "vs.message.0x800A002A"
  - "vs.message.VB_E_IDWOLENOTRESPONDING"
ms.assetid: 0a4efbb7-72de-43a8-a51a-4a7a24ec743a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft.
服务器应用程序尚未完成当前请求。  
  
 阻止某些 devenv.exe 进程的防病毒软件也可能导致此错误。  产品中的几项功能使用脚本，而这些脚本可能会被防病毒软件阻止。  有关的信息，请参见位于 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;zh\-cn;306905&Product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;zh-cn;306905&Product=vsnet) 上的“PRB: Visual IDE does not open when started or application cannot start error message”（PRB：可视化 IDE 在启动时不打开或者应用程序无法启动错误信息）。  
  
### 更正此错误  
  
-   选择“切换至”以打开应用程序并考查问题。  
  
     \- 或 \-  
  
     选择“重试”以等待服务器应用程序处理完请求。  
  
### 更正与防病毒有关的错误  
  
-   在防病毒软件中，指定该软件应当允许来自 devenv.exe 的脚本运行。  有关详细说明，请参见防病毒软件的产品文档。