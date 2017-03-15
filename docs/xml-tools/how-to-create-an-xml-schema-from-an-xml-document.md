---
title: "如何：从 XML 文档创建 XML 架构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：从 XML 文档创建 XML 架构
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用“XML 编辑器”可以从 XML 文档创建 XML 架构定义语言 \(XSD\) 架构。XML 实例文档通过以下方式确定如何生成架构：  
  
-   如果 XML 文档没有关联的架构或文档类型定义 \(DTD\)，将使用 XML 文档中的数据推断新的 XML 架构。  
  
-   如果 XML 文档包含关联的 DTD，外部 DTD 和内部子集将转换为相应的 XML 架构。  
  
-   如果 XML 文档包含内联的 XML 数据简化 \(XDR\) 架构，XDR 架构将转换为相应的 XML 架构。  
  
 然后，将使用创建的架构为 XML 文档提供智能感知。  
  
 有关架构推断引擎的更多信息，请参见[推断 XML 架构](../Topic/Inferring%20an%20XML%20Schema.md)。  
  
### 创建 XML 架构  
  
1.  将 XML 实例文档加载到“XML 编辑器”中。  
  
2.  在“工具栏”中单击“创建架构”按钮。  
  
     将为 XML 实例文档中发现的每个命名空间创建并打开一个 XML 架构文档。每个架构作为临时的杂项文件打开。  
  
     架构可以保存到磁盘中、添加到项目中或丢弃。  
  
    > [!NOTE]
    >  从“XML 编辑器”的快捷菜单中和 **XML** 菜单下也可以执行“创建架构”命令。  
  
## 请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)