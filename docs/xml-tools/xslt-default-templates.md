---
title: "XSLT 默认模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XSLT 默认模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 XSLT 处理期间，如果在样式表中没有匹配的显式模板规则，则使用默认模板。在 W3C XSLT 1.0 建议的第 5.8 节中定义了默认模板（也称为内置模板规则）。默认模板允许 XSLT 处理器处理节点，即使没有与其匹配的显式模板规则也如此。但是，因为没有在样式表中显式定义内置模板规则，所以可能导致意外的或混乱的 XSLT 转换结果。  
  
 XSLT 调试器此时显示 XSLT 默认模板的代码。当逐句通过 XSLT 转换时，如果使用默认模板，则调试器在窗口中显示默认模板。这使您能够逐句通过默认模板的代码并且按照它的说明设置断点。  
  
## 请参阅  
 [调试 XSLT](../xml-tools/debugging-xslt.md)