---
title: "IDebugSymbolProviderDirect::GetMetaDataImport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMetaDataImport"
  - "IDebugSymbolProviderDirect::GetMetaDataImport"
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMetaDataImport
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索元数据导入信息。  
  
## 语法  
  
```cpp#  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```c#  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### 参数  
 `guid`  
 \[in\] 模块的唯一标识符。  
  
 `appID`  
 \[in\] 应用程序域的标识符。  
  
 `ppImport`  
 \[out\] 返回包含元数据导入信息的对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)