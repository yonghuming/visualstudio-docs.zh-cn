---
title: "消除了 ~ SAK 文件 | Microsoft Docs"
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
  - "临时文件"
  - "~ sak 文件"
  - "源代码管理插件 ~ SAK 文件"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 消除了 ~ SAK 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在源代码管理插件 API 1.2， ~SAK 文件中函数标志和检测的新功能替换了源代码管理插件是否支持 MSSCCPRJ 文件和共享签出。  
  
## ~SAK 文件  
 Visual Studio .NET 2003 创建的临时文件加前缀 ~SAK。  这些文件用于确定源代码管理插件是否支持:  
  
-   MSSCCPRJ.SCC 文件。  
  
-   多个 \(共享\) 签出。  
  
 对于支持的插件最新机能在源代码管理插件 API 1.2 提供了， IDE 会检测到这些功能，而不必创建临时文件使用新功能，标志和功能，详细介绍以下部分。  
  
## 新功能标志  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## 新增功能  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 如果源代码管理插件支持多个 \(共享\) 签出，则声明 `SCC_CAP_MULTICHECKOUT` 功能并实现 `SccIsMultiCheckOutEnabled` 功能。  调用该函数时，每次签出操作将发生任何源代码管理项。  
  
 如果源代码管理插件支持创建和对 MSSCCPRJ.SCC 文件的使用，则声明 `SCC_CAP_SCCFILE` 功能并实现 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)。  此功能称为与文件的列表。  函数返回每个文件的 `TRUE/FALSE` 可以指示 Visual Studio 是否应针对它使用 MSSCCPRJ.SCC 文件。  如果源代码管理插件选择不支持这些新功能，它可以使用以下注册表项来禁用这些文件的创建:  
  
 \[HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateTemporaryFilesInSourceControl " \=dword: 00000001  
  
> [!NOTE]
>  如果此注册表项设置为大小: 00000000，它与中的关键字是等效的不存在的，并且， Visual Studio 仍尝试创建临时文件。  但是，因此，如果注册表项设置为大小: 00000001，则 Visual Studio 不会尝试创建临时文件。  而是假定，源代码管理插件不支持 MSSCCPRJ.SCC 文件，不支持共享签出。  
  
## 请参阅  
 [什么是源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)