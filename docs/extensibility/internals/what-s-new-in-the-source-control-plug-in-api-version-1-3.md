---
title: "什么是源代码管理插件 API 版本 1.3 中的新增功能 | Microsoft Docs"
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
  - "源代码管理插件，什么是 API v1.3 中的新增功能"
  - "什么是新 [Visual Studio SDK]，源代码管理插件"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 什么是源代码管理插件 API 版本 1.3 中的新增功能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

源代码管理插件 API 1.3 版中引入下列新的功能提供高级控件。  
  
## 更改  
 以下功能不熟悉源代码管理插件 API 版本 1.3:  
  
|功能|概述|  
|--------|--------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|允许其他功能位报告|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|允许具有新在版本控制数据库比在本地磁盘上的物理文件|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|允许名称更改状态的检查 \(重命名，添加和删除\) 中指定的文件|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|允许目录和文件的物理在版本控制数据库中|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|将指定的列表从版本控制数据库的文件添加到当前项目|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|执行 " 无 “get”中指定的文件 \(用户界面不显示\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|允许访问用户特定的选项的访问|  
  
## 请参阅  
 [入门](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [什么是源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)