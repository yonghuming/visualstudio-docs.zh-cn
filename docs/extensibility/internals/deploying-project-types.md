---
title: "部署项目类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7673839e44e913d7d0a219400142fe7e6a0b95e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-project-types"></a>部署项目类型
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]安装新的项目类型聚合器 (ProjectAggregator2.dll) 以及 Windows Installer 程序包以进行重新分发 (ProjectAggregator2.msi)。 对托管代码项目类型，必须使用新的聚合器。 ProjectAggregator2 方法限制适用于[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目导致无法正常工作的托管代码项目类型的聚合器。 以下步骤介绍如何更改你的 VSPackage 来使用新的聚合器。  
  
1.  从解决方案中移除 NativeHierarchyWrapper 项目。  
  
2.  从你的设置中删除任何 NativeHierarchyWrapper 二进制文件。  
  
3.  将 ProjectAggregator2.msi 添加到你的设置。