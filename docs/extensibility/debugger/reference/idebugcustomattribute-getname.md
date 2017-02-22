---
title: "IDebugCustomAttribute::GetName | Microsoft Docs"
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
  - "IDebugCustomAttribute::GetName"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetName"
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取自定义属性的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```c#  
int GetName(  
   out string bstrName  
);  
```  
  
#### 参数  
 `bstrName`  
 \[out\] 返回包含自定义特性的名称的字符串。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 名为的此方法返回对应于用于的类的名称声明属性。  这可能无法正确对应于自定义特性类的名称，当 c\# 允许使用 “属性”后缀从自定义属性名称下降，如果在声明时。  
  
## 请参阅  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)