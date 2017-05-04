---
title: "IJsEnumDebugProperty::Next 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsEnumDebugProperty::Next 方法
读取此对象的属性。  
  
## 语法  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### 参数  
 `count`  
 \[in\] 读取属性的数目。  
  
 `ppDebugProperty`  
 \[out\] 表示属性浏览器的对象。  
  
 `pActualCount`  
 \[out\] 对象的属性的实际数目。  
  
## 返回值  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsEnumDebugProperty 接口](../../winscript/reference/ijsenumdebugproperty-interface.md)