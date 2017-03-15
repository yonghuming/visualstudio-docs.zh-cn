---
title: "IDebugProgramNode2::GetProgramName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetProgramName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetProgramName"
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取程序的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```c#  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### 参数  
 `pbstrProgramName`  
 \[out\] 返回程序的名称。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 程序的名称不是内容和路径与对程序，不过，程序的名称可以是此路径的一部分。  
  
## 示例  
 下面的示例演示如何执行简单的 `CProgram` 对象的方法实现 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 接口。  `MakeBstr` 函数将指定字符串的副本作为 BSTR。  
  
```cpp#  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## 请参阅  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)