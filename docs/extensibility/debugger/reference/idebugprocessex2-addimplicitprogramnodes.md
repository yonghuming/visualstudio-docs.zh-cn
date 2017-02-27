---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes 方法"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法将每一个的过程节点调试引擎 \(DE\)指定。  
  
## 语法  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### 参数  
 `guidLaunchingEngine`  
 \[in\] 将使用启动程序 DE 的 `GUID` \(和假定添加自己的程序节点\)。  
  
 `rgguidSpecificEngines`  
 \[in\] 数组 `GUID`程序节点将添加 DES 的。  
  
 `celtSpecificEngines`  
 \[in\] `GUID`的数。 `rgguidSpecificEngines` 数组。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 [程序节点](../../../extensibility/debugger/program-nodes.md) 为 `rgguidSpecificEngines`列表的每个 DE 将添加 \(但生成的引擎 \(如对 `guidLaunchingEngine`\)，假定添加自己的程序节点，则启动程序。  
  
## 请参阅  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [程序节点](../../../extensibility/debugger/program-nodes.md)