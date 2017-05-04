---
title: "函数没有有效的原型对象 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 函数没有有效的原型对象
尝试使用 **instanceof** 来确定对象是否是从特定函数类派生的，但是将对象的 `prototype` 属性重新定义为 `null` 或外部对象类型（都不是有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象）。  外部对象可以是宿主对象模型中的对象（例如，Internet Explorer 的文档或窗口对象）或外部 COM 对象。  
  
### 更正此错误  
  
-   确保函数的 `prototype` 属性引用有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  
  
## 请参阅  
 [Function 对象](../../javascript/reference/function-object-javascript.md)   
 [prototype 属性（对象）](../../javascript/reference/prototype-property-object-javascript.md)