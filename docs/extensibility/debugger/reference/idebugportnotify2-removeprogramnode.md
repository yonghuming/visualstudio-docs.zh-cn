---
title: "IDebugPortNotify2::RemoveProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortNotify2::RemoveProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

程序可以从该端口在调试运行它的注销。  
  
## 语法  
  
```cpp#  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### 参数  
 `pProgramNode`  
 \[in\] 表示程序中注销 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objecy。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法会移除添加具有调入 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 方法的过程节点。  
  
## 请参阅  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)