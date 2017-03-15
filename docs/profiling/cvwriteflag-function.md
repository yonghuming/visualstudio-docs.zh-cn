---
title: "CvWriteFlag 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteFlagExVA"
  - "cvmarkers/CvWriteFlagExW"
  - "cvmarkers/CvWriteFlagExVW"
  - "cvmarkers/CvWriteFlagExA"
helpviewer_keywords: 
  - "CvWriteFlagExW 方法"
  - "CvWriteFlagExVA 方法"
  - "CvWriteFlagExA 方法"
  - "CvWriteFlagExVW 方法"
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# CvWriteFlag 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将标志写入并发可视化工具跟踪文件。  
  
## 语法  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### 参数  
 `argList`  
 参数列表。  
  
 `category`  
 分类  
  
 `level`  
 重要程度。  
  
 `pMarkerSeries`  
 有效标记系列上下文。  不能为 NULL。  
  
 `pMessage`  
 消息格式字符串。  不能为 NULL。  
  
## 返回值  
 S\_OK，当消息成功写入。  错误代码，当有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
 **Unicode:** CvWriteFlagExW，CvWriteFlagExVW  
  
 **ANSI:**CvWriteFlagExA，CvWriteFlagExVA  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)