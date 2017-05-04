---
title: "无法给“this”赋值 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 无法给“this”赋值
尝试为 **this** 赋值。  **this** 是引用以下任一项的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 关键字：  
  
-   当前正在执行方法的对象，  
  
-   全局对象（如果没有当前方法或方法不属于其他任何对象）。  
  
 方法是通过对象调用的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 函数。  在方法中，**this** 关键字是对通过其调用方法的对象（正好是通过调用带有 **new** 运算符的类构造函数所创建的对象）的引用。  
  
 在方法中，您可以使用 **this** 来引用当前对象，但不能将新的值赋给 **this**。  
  
### 更正此错误  
  
-   不要尝试为 **this**  赋值。  若要访问实例化对象的属性或方法，请使用点运算符（例如 circle**.**radius）。  
  
    > [!NOTE]
    >  不能将用户创建的变量命名为 **this**；它是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的保留字。  
  
## 请参阅  
 [this 语句](../../javascript/reference/this-statement-javascript.md)   
 [脚本疑难解答](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)