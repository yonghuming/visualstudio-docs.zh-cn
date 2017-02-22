---
title: "IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs"
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
  - "IDebugCustomAttribute::GetAttributeBytes"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取属性信息作为字节 blob。  
  
## 语法  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```c#  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### 参数  
 `ppBlob`  
 \[in, out\] 用特性字节填充的数组。  
  
 `pdwLen`  
 \[in, out\] 在 `ppBlob` 数组指定最大字节数返回并返回到数组实际上编写字节数。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 设置 `ppBlob` 参数设置为空值返回属性的字节数。可用。  然后将一个数组并为 `ppBlob` 参数将该数组。  
  
 属性字节表示自定义属性的原始数据。  
  
## 请参阅  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)