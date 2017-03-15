---
title: "IEnumDebugReferenceInfo2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2::Reset"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Reset"
ms.assetid: cf8ce649-5ce1-44a6-9d5a-89760021bde4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugReferenceInfo2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

重置枚举到第一个元素。  
  
## 语法  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法调用之后，下调用 [下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md) 方法返回枚举中的第一个元素。  
  
## 请参阅  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)