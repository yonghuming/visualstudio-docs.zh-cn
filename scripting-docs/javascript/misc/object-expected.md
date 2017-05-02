---
title: "应为 Object | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5007"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 应为 Object
你尝试调用了 `Object` 类型以外的对象上的方法或属性，或在需要 `Object` 时传递了 `Object` 类型以外的参数。  
  
### 更正此错误  
  
-   仅调用类型为 `Object` 的对象上的方法或属性。  
  
-   如果非对象参数发生错误，则传递类型为 `Object` 的对象。  
  
-   检查是否正在调用未定义的或 null 引用而不是类型为 `Object` 的对象。  
  
     例如，如果以下代码的 myVar 上出现此错误：  
  
    ```javascript  
    var str = myVar.toString();  
    ```  
  
     可改用以下代码：  
  
    ```javascript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## 请参阅  
 [Object 对象](../../javascript/reference/object-object-javascript.md)   
 [对象和数组](../../javascript/objects-and-arrays-javascript.md)