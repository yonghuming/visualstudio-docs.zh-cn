---
title: "CvCreateDefaultMarkerSeriesOfDefaultProvider 函数 | Microsoft Docs"
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
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider 方法"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateDefaultMarkerSeriesOfDefaultProvider 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建默认提供程序的默认标记系列。  
  
## 语法  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### 参数  
 `ppProvider`  
 提供程序对象变量的地址。  地址不能为 null，此变量可以具有任何值。  
  
 `ppMarkerSeries`  
 地址标记系列对象变量。  地址不能为 null，此变量可以具有任何值。  
  
## 返回值  
 S\_OK，当提供程序和标记系列成功创建或有错误代码以防有任何错误。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)