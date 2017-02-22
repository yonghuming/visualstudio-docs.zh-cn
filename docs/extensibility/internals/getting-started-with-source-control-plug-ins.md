---
title: "开始使用源代码管理插件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件入门"
  - "获取已启动，源代码管理插件"
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 开始使用源代码管理插件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要创建源代码管理插件，必须创建一个实现在源代码管理插件 API 定义的函数的 DLL，以注册 DLL 是用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 并使其可用于源代码版本控制。  
  
 源代码管理插件 API 的三个版本 \(1.1 版，版本 1.2 和版本 1.3\) 为源代码管理插件可用。  文档的源代码管理插件 API 此处 1.3 版。  它旨在完全兼容。与支持 1.1 版和 1.2 版的源代码管理插件。  [什么是源代码管理插件 API 版本 1.3 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) 一节详细描述在源代码管理插件 API 的最新版本支持的新功能。  
  
## 本节内容  
 [如何: 安装了源代码管理插件](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 描述如何进行需要在源代码管理 DLL 的注册表项。  
  
 [什么是源代码管理插件 API 版本 1.3 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 提供对 1.3 版的源代码管理插件 API 更改的简短概述。  
  
 [什么是源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 提供对 1.2 版的源代码管理插件 API 更改的简短概述。  
  
## 相关章节  
 [源代码管理插件](../../extensibility/source-control-plug-ins.md)  
 提供完整列表在源代码管理插件 API 的所有元素。  
  
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 定义源代码管理插件 SDK 并描述包含的资源。