---
title: "持久性和运行 Document 表 | Microsoft Docs"
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
  - "持久性、 管理"
  - "IVsPersistHierarchyItem 接口实现"
  - "持久性的体系结构"
  - "正在运行的 document 表 (RDT) 体系结构"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 持久性和运行 Document 表
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中，项目是完全负责管理他们完成使用服务，其项目项的持久性 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 文档是 Visual Studio 环境中的暂留的基本单位。 项目协调打开、 保存和重命名的文档与正在运行文档表 \(RDT\) 跟踪所有打开的文档的状态的资源。  
  
## 管理持久性  
 项目通过实施控制环境的持久性服务 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 接口。 虽然环境永远不会直接询问要保持自身的文档时，它会询问所属项目 \(或层次结构\) 来保存文档。 这使项目及其项目项数据保存到本地文件、 远程文件、 数据库、 一个存储库或其他媒体。  
  
 全局环境维护 RDT。 环境维护所有打开的窗口的条目并 RDT，这样就可以由他们中的文档接收特殊的通知，例如关闭时，一种解决方案。 此外，RDT 使环境来跟踪在其相应节点 **解决方案资源管理器**。 RDT 维护每个开放的、 持久的对象，包括项目文件和项目项文档的一条记录。  
  
## 请参阅  
 [正在运行的 Document 表](../../extensibility/internals/running-document-table.md)   
 [所选内容和在 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)