---
title: "JsProjectWinRTNamespace 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8a23c154-df4b-4ce3-9fef-f41f90acdb87
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsProjectWinRTNamespace 函数
投影 WinRT 命名空间。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode)  
   JsProjectWinRTNamespace(  
   _In_z_ const wchar_t *namespaceName  
);  
```  
  
#### 参数  
 `namespaceName`  
 要投影的 WinRT 命名空间。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
> [!NOTE]
>  WinRT 是通用 Windows 平台 \(UWP\) 之前的平台名称。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)