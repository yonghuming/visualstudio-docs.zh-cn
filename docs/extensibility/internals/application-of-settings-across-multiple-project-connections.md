---
title: "跨多个项目连接设置应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件，应用程序的设置"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 跨多个项目连接设置应用程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用源代码管理插件 API 生成的源代码管理插件 1.2，可以使用批处理操作执行在多个项目或多个连接上下文中的同一源代码管理操作。  批处理可用于消除冗余，从用户体验的每个项目的对话框。  
  
 如果用户选择属于多个在使用源代码管理插件 API 编译的源代码管理插件中的连接 1.1 的多个项目， \(例如，在不同的文件共享设备的两个 Web 项目\) 并进行检查，用户重复看到对话框相同。  发生这种情况，即使用户在对话框中单击 **适用于任何** 复选框，，因为 IDE 重置其每个连接上下文的状态。  
  
## 新功能标志  
 `SccBeginBatch` 功能集 `SCC_CAP_BATCH` 标志指示批处理操作正在进行  
  
## 新增功能  
 以下新功能支持批处理操作:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch` 函数启动源代码管理操作的一组。  `SccEndBatch` 关闭组。  组不能嵌套。  
  
## 请参阅  
 [什么是源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)