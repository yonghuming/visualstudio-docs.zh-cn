---
title: "比较到源代码管理存储区的项目文件夹 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cde0a7c34fe81c86d9f500bb1800006e5291ee92
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>到源代码管理存储区的本地项目文件夹的可选比较
在源中控制本地项目文件夹和源控件之间的比较通过使用函数来实现的插件 API 1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)。  
  
 在**解决方案资源管理器**，如果而不是单个文件，选择文件夹**比较版本**快捷菜单时，将调用新[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)在源代码管理插件。  
  
## <a name="new-capability-flags"></a>新功能标志  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>新的函数  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`函数调用前`SccDirDiff`以确定是否受源代码管理的工作目录。 `SccDirDiff`函数将显示当前的本地目录和相应的源代码管理文件夹之间的差异。 此命令会询问源代码管理插件以向目录中显示的更改的列表。 源代码管理插件提供其自己的 UI，以显示了差异。  
  
> [!NOTE]
>  此函数使用相同的命令标志作为[SccDiff](../../extensibility/sccdiff-function.md)。 作为源代码管理插件提供，你可以选择不支持目录的"快速差异"操作。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)