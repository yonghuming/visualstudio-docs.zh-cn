---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

添加用户信息到图像诊断 *HUD* \(Head\-Up Display\)。  
  
## 语法  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### 参数  
 `szMessage`  
 把消息添加到 HUD。  
  
## 备注  
 图像诊断 HUD 显示在运行于图像诊断下的 app 的左上角。  它显示有关应用程序运行时的信息及有关图形信息捕捉，并通过调用这个成员函数添加消息运行时信息。  
  
 添加信息到HUD，你不必必须捕捉图像信息，也就是说，一个信息可以被添加到可替代的 `VsgDbg` 类，但 [Init](../debugger/init.md) 成员函数不能先被调用。  消息被显示在 HUD 中，则不会记录在图像日志文件中。