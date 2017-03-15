---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame::get_rawLVarInstanceValue 方法"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

此方法检索指定的局部变量的值作为原始的字节。  
  
## 语法  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### 参数  
 `pInstance`  
 \[in\] 表示局部变量访问的实例 `IDiaLVarInstance` 对象值。  
  
 `cbDataMax`  
 \[in\] 最大字节数缓冲区中的指向由 `pbData`。  这可能是最多 8 个字节 \(`sizeof(ULONGLONG)`\)。  
  
 `pcbData`  
 \[out\] 返回缓冲区存储实际字节数。  
  
 `pbData`  
 \[out\] 将用数据填充的缓冲区。  该类型不能为 `NULL`。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)