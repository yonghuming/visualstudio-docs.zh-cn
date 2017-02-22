---
title: "CvReleaseProvider 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider 方法"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvReleaseProvider 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发布标记提供程序。  发布标记提供程序不会影响此提供程序创建之前的标记。  标记系列必须分别会释放由 CvReleaseMarkerSeries 调用。  如果释放提供程序会导致内存泄漏。  
  
## 语法  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### 参数  
 `pProvider`  
 提供程序上下文。  不能为 NULL。  
  
## 返回值  
 S\_OK，当提供程序成功发布或错误代码当有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)