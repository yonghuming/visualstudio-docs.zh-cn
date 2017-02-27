---
title: "IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetHostMachineName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostMachineName_V7"
  - "IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName"
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

已弃用。  不要使用。  
  
## 语法  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```c#  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### 参数  
 `pbstrHostMachineName`  
 \[out\] 返回程序运行的计算机的名称。  
  
## 返回值  
 实现应始终返回 `E_NOTIMPL`。  
  
## 备注  
  
> [!WARNING]
>  自 [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]，不再使用此方法应始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)