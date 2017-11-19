---
title: "搜索架构集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6bef5c0358ecdadb5f8f9aada4e69d748b3fa14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="searching-the-schema-set"></a>搜索架构集
使用 XML 架构资源管理器，您可以通过下列方式在架构集中执行搜索：  
  
-   关键字搜索。  
  
-   特定于架构的搜索。  
  
## <a name="keyword-search"></a>关键字搜索  
 通过输入中的子字符串执行关键字搜索**搜索架构集**的 XML 架构资源管理器工具栏上的文本框。  
  
 ![XML 架构资源管理器关键字搜索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML 架构资源管理器在架构集中搜索以下内容：  
  
-   与指定关键字匹配的任何 `name` 或 `ref` 特性。 这样，您可以按名称来查找元素、特性、类型等。  
  
-   包括语句的 `schemaLocation` 特性。  
  
-   导入语句的 `namespace` 特性。  
  
## <a name="schema-specific-search"></a>特定于架构的搜索  
 XML 架构资源管理器中还包含一些内置搜索，可使用 XML 架构资源管理器的上下文菜单访问这些搜索。 有关可用的上下文菜单的详细信息，请参阅[上下文菜单](../xml-tools/context-menus-xml-schema-explorer.md)。 您还可以通过以下方式执行特定于架构的搜索从起始视图;有关详细信息，请参阅中的"架构集详细信息"部分[起始视图](../xml-tools/start-view.md)主题。  
  
## <a name="displaying-and-navigating-search-results"></a>显示和导航搜索结果  
 完成搜索后，摘要结果窗格会添加到工具栏中，其中显示搜索的结果。 搜索结果还会突出显示在 XML 架构资源管理器中，并用垂直滚动条上的刻度标记。 你可以通过使用导航搜索结果**转到下一个搜索结果**和**转到上一个搜索结果**摘要结果窗格中的 XML 架构资源管理器工具栏; 通过使用键盘键上的按钮F3 和 Shift + F3;或单击滚动条中的刻度线。  
  
 你可以向工作区添加搜索结果，通过单击**将突出显示的节点添加到工作区**摘要结果窗格上的按钮。  
  
 ![XML 架构资源管理器搜索结果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>清除搜索结果  
 若要清除搜索结果，请单击**x** XML 架构资源管理器搜索工具栏的摘要结果窗格上的按钮。  
  
## <a name="see-also"></a>另请参阅  
 [XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)