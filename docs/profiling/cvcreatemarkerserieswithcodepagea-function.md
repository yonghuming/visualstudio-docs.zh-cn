---
title: "CvCreateMarkerSeriesWithCodePageA 函数 | Microsoft Docs"
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
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA 方法"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateMarkerSeriesWithCodePageA 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

为给定提供程序和指定代码页创建标记系列。  此函数可用于标记 API ANSI 函数写出的文本显式指定代码页。  设置代码页对不同计算机使用不同的区域设置或语言来捕获然后分析跟踪非常有用。  默认情况下使用 GetACP\(\) 函数返回的代码页。  
  
## 语法  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### 参数  
 `pProvider`  
 提供程序对象先前由 CvInitProvider 初始化。  不能为 NULL。  
  
 `pSeriesName`  
 标记系列名称。  不能包括 NULL，但允许空字符串。  
  
 `nTextCodePage`  
 无效的代码页  
  
 `ppMarkerSeries`  
 输出变量的地址将会存储标记系列上下文。  不能为 NULL。  
  
## 返回值  
 S\_OK，当标记系列成功创建或有错误代码以防有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)