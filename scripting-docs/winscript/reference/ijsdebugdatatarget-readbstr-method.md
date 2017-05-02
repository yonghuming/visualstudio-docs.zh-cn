---
title: "IJsDebugDataTarget::ReadBSTR 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadBSTR 方法
从调试目标中读取 BSTR。  
  
## 语法  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### 参数  
 `address`  
 \[in\] 要从中读取的地址。  
  
 `pString`  
 \[out\] 从调试目标读取的 BSTR。  
  
## 返回值  
  
## 备注  
 如果地址无效，则返回 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugDataTarget 接口](../../winscript/reference/ijsdebugdatatarget-interface.md)