---
title: "MSBuild 错误 MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB8031
MSB8031  
  
 要在 MFC 项目中使用 MBCS 编码，你必须下载和安装其他的库。  
  
 MFC DLL 的 MBCS 版不包含于 Visual Studio 中，但是可用于 MFC MBCS DLL 插件。如果您是 Visual Studio 用户，可以下载。  如果不安装加载项就尝试生成使用 MBCS 字符集的 MFC 项目，则链接器会找不到 DLL，生成失败。  
  
### 更正此错误  
  
1.  [Download the MBCS MFC DLL Add\-on](http://go.microsoft.com/fwlink/?LinkId=299009)（下载 MBCS MFC DLL 加载项），从 MSDN 下载中心，或将您的项目转换为 UNICODE 字符集（如果可执行此操作）。  
  
## 请参阅  
 [MFC MBCS DLL 加载项](/visual-cpp/mfc/mfc-mbcs-dll-add-on)