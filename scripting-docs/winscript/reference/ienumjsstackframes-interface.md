---
title: "IEnumJsStackFrames 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames 接口
由调试器实现，以提供对 JavaScript 的 jscript9diag.dll 展开的堆栈。  
  
## 语法  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IEnumJsStackFrames::Next 方法](../../winscript/reference/ienumjsstackframes-next-method.md)|获取帧的指定的数。|  
|[IEnumJsStackFrames::Reset 方法](../../winscript/reference/ienumjsstackframes-reset-method.md)|重置堆栈帧为第一个元素之前的位置。|  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)