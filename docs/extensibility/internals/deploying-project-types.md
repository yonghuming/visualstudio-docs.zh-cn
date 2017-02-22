---
title: "部署项目类型 | Microsoft Docs"
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
  - "项目 [Visual Studio SDK]，托管代码"
  - "项目 [Visual Studio SDK]，聚合函数"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 部署项目类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 安装新的项目类型聚合函数 \(ProjectAggregator2.dll\) 以及重新分发 \(ProjectAggregator2.msi\) 是 Windows 安装程序包。 为托管代码的项目类型，则必须使用新的聚合函数。 ProjectAggregator2 方法限制适用于 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目导致无法正常工作的托管代码项目类型的聚合函数。 以下步骤介绍如何更改你的 VSPackage，若要使用新的聚合函数。  
  
1.  从解决方案中移除 NativeHierarchyWrapper 项目。  
  
2.  从您的安装程序中删除任何 NativeHierarchyWrapper 二进制文件。  
  
3.  将 ProjectAggregator2.msi 添加到您的安装程序。