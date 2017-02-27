---
title: "CvInitProvider 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider 方法"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvInitProvider 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

初始化标记提供程序。  必须在任何其他并发可视化工具 SDK 函数之前调用。  
  
## 语法  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### 参数  
 `pGuid`  
 guid 提供程序。  不能为 NULL。  
  
 `ppProvider`  
 要存储输出提供程序上下文变量的地址。  不能为 NULL。  
  
## 返回值  
 S\_OK，当提供程序成功初始化或错误代码当有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)