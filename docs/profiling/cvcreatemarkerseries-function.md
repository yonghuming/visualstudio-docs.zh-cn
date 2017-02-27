---
title: "CvCreateMarkerSeries 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA 方法"
  - "CvCreateMarkerSeriesW 方法"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeries 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建特定提供程序的标记之前。  
  
## 语法  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### 参数  
 `pProvider`  
 提供程序对象先前由 CvInitProvider 初始化。  不能为 NULL。  
  
 `pSeriesName`  
 标记系列名称。  不能包括 NULL，但允许空字符串。  
  
 `ppMarkerSeries`  
 输出变量的地址将会存储标记系列上下文。  不能为 NULL。  
  
## 返回值  
 S\_OK，当标记系列成功创建或有错误代码以防有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)