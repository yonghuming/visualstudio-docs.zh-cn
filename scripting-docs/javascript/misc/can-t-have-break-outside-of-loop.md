---
title: "“break”不能位于循环外 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# “break”不能位于循环外
尝试在循环外部使用 **break** 关键字。  **break** 关键字用于终止循环或 `switch` 语句。  它必须嵌入到循环体或 `switch` 语句中。  但是，**label** 可紧跟 break 关键字。  
  
```  
break labelname;  
```  
  
 仅当您使用嵌套循环或 `switch` 语句并需要中断非最里面的循环时，需要标签形式的 **break** 关键字。  
  
### 更正此错误  
  
-   确保 **break** 关键字显示在封闭循环或 switch 语句中。  
  
## 请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [控制程序流](../../javascript/controlling-program-flow-javascript.md)   
 [脚本疑难解答](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)