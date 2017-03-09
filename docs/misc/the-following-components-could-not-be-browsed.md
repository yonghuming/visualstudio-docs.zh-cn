---
title: "The following components could not be browsed: | Microsoft Docs"
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
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The following components could not be browsed:
此消息框可以列出与“对象浏览器”和“组件选择”对话框相关的多个错误。  下列错误是一些最常见的错误。  
  
## 组件或文件类型无法在“对象浏览器”中查看。  
 当指定的文件名不存在或无效时或者指定无法通过“对象浏览器”浏览的文件时，通常会发生此错误。  
  
#### 更正此错误  
  
-   验证指定的文件名是否存在并且是可浏览的组件，如 .NET 程序集、COM 类型库或源浏览器文件。  
  
## 文件不是有效的 .NET Framework 或 COM 组件。  
 当指定的组件不是 .NET Framework 程序集或 COM 类型库时，通常会发生此错误。  
  
#### 更正此错误  
  
-   选择另一个要浏览的组件。  
  
## 文件无法作为 COM 组件进行注册。  
 当无法注册 COM 组件的类型库时，通常会发生此错误。  该类型库可能不存在或可能已损坏。  
  
#### 更正此错误  
  
-   重新安装此组件，然后重试。  
  
## 未注册匹配的类型库，或注册的信息无效。  
 指定的类型库可能不再存在，或者可能没有包含有效信息。  
  
#### 更正此错误  
  
-   验证类型库是否存在且正确注册。  
  
## 缺少浏览 COM 类型库所需的组件，或该组件未正确注册。  
 缺少文件 vstlbinf.dll 或者没有正确注册该文件。  
  
#### 更正此错误  
  
1.  在计算机上找到 vstlbinf.dll，然后使用 regsvr32.exe 注册它。  
  
     \- 或 \-  
  
2.  如果在计算机上无法找到 vstlbinf.dll，则重新安装此产品。  
  
## 请参阅  
 [Object Browser](http://msdn.microsoft.com/zh-cn/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/zh-cn/dc995bd7-afbf-4389-ba1c-f377b677ded7)