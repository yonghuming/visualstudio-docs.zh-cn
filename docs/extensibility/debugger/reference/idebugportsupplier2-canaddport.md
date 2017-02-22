---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

验证端口提供程序可以添加新端口。  
  
## 语法  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## 返回值  
 如果端口可以添加，则返回; `S_OK`否则，返回 `S_FALSE` 指示该端口不允许添加到此端口提供程序。  
  
## 备注  
 在调用 [添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 方法之前调用此方法，因为之后方法创建端口以及添加它，可能会非常耗时的操作。  
  
## 请参阅  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)