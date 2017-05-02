---
title: "Debug.setNonUserCodeExceptions 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Debug.setNonUserCodeExceptions 属性
确定调试器是否会将此范围内的任何 try\-catch 块视为用户未处理的。  可将异常分类为引发、用户未处理的或未处理的。  
  
 在给定范围内将此属性设置为 `true` 的情况下，如果开发人员希望中断用户未处理的异常，则调试器会确定对该范围内引发的异常执行某项操作（如中断）。  在将此属性设置为 `false` 时，就好像从未设置该属性一样。  
  
 有关调试的更多信息，请参见[活动脚本调试概述](http://go.microsoft.com/fwlink/p/?LinkId=249469)。  
  
## 语法  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## 示例  
 下面的代码演示如何设置此属性。  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]