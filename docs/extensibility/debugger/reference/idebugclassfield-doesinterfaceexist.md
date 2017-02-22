---
title: "IDebugClassField::DoesInterfaceExist | Microsoft Docs"
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
  - "IDebugClassField::DoesInterfaceExist"
helpviewer_keywords: 
  - "IDebugClassField::DoesInterfaceExist 方法"
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定特定接口是否在类中定义。  
  
## 语法  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```c#  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### 参数  
 `pszInterfaceName`  
 \[in\] 包含接口名称的字符串查找。  
  
## 返回值  
 如果成功，则返回 S\_OK，返回 S\_FALSE，如果接口不存在;否则，返回错误代码。  
  
## 备注  
 此方法实际获取所有接口的枚举并搜索列表匹配的接口。  
  
## 请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)