---
title: "CvReleaseMarkerSeries 函数 | Microsoft Docs"
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
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries 方法"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvReleaseMarkerSeries 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

发布标记系列。  在发布之后请勿使用标记系列对象，否则应用程序可能会崩溃。  发布失败的标记系列会导致内存泄漏。  
  
## 语法  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### 参数  
 `pMarkerSeries`  
 提供程序对象变量的地址。  地址不能为 null，此变量可以具有任何值。  
  
## 返回值  
 S\_OK，当标记系列成功发布或错误代码以防有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)