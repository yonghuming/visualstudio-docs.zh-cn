---
title: "IDebugDefaultPort2::QueryIsLocal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::QueryIsLocal"
helpviewer_keywords: 
  - "IDebugDefaultPort2::QueryIsLocal"
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDefaultPort2::QueryIsLocal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法确定此端口是否在本地计算机上。  
  
## 语法  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```c#  
int QueryIsLocal();  
```  
  
## 返回值  
 返回 `S_OK` ，则此端口是本地路径 \(在计算机和调用方相同\) 或 `S_FALSE` ，如果该端口在另一台计算机。  
  
## 请参阅  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)