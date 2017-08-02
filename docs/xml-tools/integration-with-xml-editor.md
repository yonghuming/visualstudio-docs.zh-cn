---
title: "与 XML 编辑器的集成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# 与 XML 编辑器的集成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 编辑器中集成了 XML 架构设计器。如果在 XML 编辑器中修改 XSD 文件，则更改将会反映在 [XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)中。如果[图形视图](../xml-tools/graph-view.md)或[内容模型视图](../xml-tools/content-model-view.md)处于打开状态，则更改也会反映在其中。可通过以下方法在 XML 架构设计器和 XML 编辑器之间导航：  
  
-   在 XML 编辑器中，右击某个节点并选择**“在 XML 架构资源管理器中显示”**。  
  
-   在图形视图和 XML 架构资源管理器中，双击某个节点，或右击某个节点并选择**“查看代码”**。在内容模型视图中，右击某个节点并选择**“查看代码”**。  
  
 以下屏幕快照显示了在 XML 架构资源管理器中打开的某个 XML 架构。XML 架构资源管理器在树视图中显示架构集。XML 编辑器显示当前在 XML 架构资源管理器中处于活动状态的节点的文本视图。  
  
 ![XSDDesignerWithXMLEditor](~/docs/xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
 有时，在 XML 编辑器中和在图形设计器中并行查看代码是很有帮助的。若要同时查看两个文件，请右击 XML 编辑器中的任意位置并选择**“视图设计器”**。在“Visual Studio Windows”菜单中，选择**“新建水平 \(或垂直\) 选项卡组”**。  
  
 ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## 请参阅  
 [XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)