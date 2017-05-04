---
title: "ICanHandleException 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ICanHandleException 接口"
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException 接口
允许脚本引擎的调用方指定哪些异常调用方处理。  
  
## 方法  
 除了从 `IUnknown` 继承的方法之外，`ICanHandleException` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|确定脚本引擎的调用方是否可以处理指定的异常。|