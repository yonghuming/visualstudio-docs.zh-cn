---
title: "提供的服务 (源控制 VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服务、 源代码管理包"
  - "源代码管理包服务"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 提供的服务 (源控制 VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

服务是共享函数在 Vspackage 中和 Visual Studio 集成开发环境及其安装的 sharepoint 项目服务之间 \(IDE\)的主要机制。  有关详细说明服务及其关键在 Visual Studio IDE，请参见[使用并提供服务](../../extensibility/using-and-providing-services.md)。  
  
## 源代码管理服务  
 Visual Studio 提供服务、 IDE 级别服务和包级别服务两个层。  Visual Studio IDE 本身提供 IDE 级别服务。  源代码管理包使用其中的一些服务。  源控件打包成 VSPackage 通过提供自己的专用源代码管理服务共享其源代码管理功能。  源代码管理包封装一组它实现的源代码管理相关的接口以可由 Visual Studio IDE 使用的协定的形式。  
  
## 请参阅  
 [设计元素](../../extensibility/internals/source-control-vspackage-design-elements.md)