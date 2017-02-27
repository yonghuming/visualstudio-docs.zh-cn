---
title: "如何︰ 通过使用注册表设置管理专用库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 私有库，也管理"
  - "管理私有库也 VSIX"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何︰ 通过使用注册表设置管理专用库
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您是管理员或独立 Shell 扩展插件的开发人员，您可以控制对控件、 模板和工具 Visual Studio 库、 示例库或私有的库中访问。 若要使库可用或不可用，请创建介绍修改过的注册表项和它们的值的.pkgdef 文件。  
  
## 管理专用库  
 您可以创建一个.pkgdef 文件，以控制对多台计算机上的库的访问。 此文件必须具有以下格式。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` 键是指库以启用或禁用。 Visual Studio 库和示例库使用以下存储库中的 Guid:  
  
-   Visual Studio 库︰ 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   示例库︰ AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 `Disabled` 值是可选的。 默认情况下，一个库，处于启用状态。  
  
 `Priority` 值确定在选项对话框中列出库的顺序。 Visual Studio 库具有优先级为 10，示例库具有 20 的优先级。 私有库也在优先级 100 处开始。 如果多个库具有相同的优先级值，它们出现的顺序由其本地化的值 `DisplayName` 属性。  
  
 `Protocol` 值是必需的基于 Atom 的或基于 SharePoint 的库。  
  
 要么 `DisplayName`, ，和 \/ 或 `DisplayNameResourceID` 和 `DisplayNamePackageGuid`, ，必须指定。 如果所有未指定，则 `DisplayNameResourceID` 和 `DisplayNamePackageGuid` 使用对。  
  
## 禁用 Visual Studio 库使用.pkgdef 文件  
 您可以禁用.pkgdef 文件中的库。 以下项可以禁用 Visual Studio 库︰  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 以下项可以禁用示例库︰  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## 请参阅  
 [私有库](../extensibility/private-galleries.md)