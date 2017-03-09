---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
当从项目文件中移除引用时遇到错误。  此错误的原因在 \<原因\> 中标识，可能是由于：  
  
-   格式错误的用于引用的 GUID。  这仅适用于 COM 引用。  
  
-   错误的包装工具。  目前，包装工具属性可以是 tlbimp、aximp 或 primary 中的一个。  这仅适用于 COM 引用。  
  
-   错误的项目引用字符串。  这仅适用于项目到项目的引用。  
  
 **更正此错误**  
  
-   将该引用添加到项目以解决此错误。  
  
     不会将任何为其显示该诊断的引用加载到项目中。  
  
## 请参阅  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)