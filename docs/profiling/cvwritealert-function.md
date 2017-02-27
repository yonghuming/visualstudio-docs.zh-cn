---
title: "CvWriteAlert 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteAlertVA"
  - "cvmarkers/CvWriteAlertVW"
  - "cvmarkers/CvWriteAlertA"
  - "cvmarkers/CvWriteAlertW"
helpviewer_keywords: 
  - "CvWriteAlertVW 方法"
  - "CvWriteAlertA 方法"
  - "CvWriteAlertVA 方法"
  - "CvWriteAlertW 方法"
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# CvWriteAlert 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将警报写入并发可视化工具跟踪文件。  
  
## 语法  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### 参数  
 `argList`  
 参数列表。  
  
 `pMarkerSeries`  
 有效标记系列上下文。  不能为 NULL。  
  
 `pMessage`  
 消息格式字符串。  不能为 NULL。  
  
## 返回值  
 S\_OK，当消息成功写入。  错误代码，当有任何错误时。  使用 SUCCEEDED\/FAILED 宏检查错误状态。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
 **Unicode:** CvWriteAlertW，CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA，CvWriteAlertVA  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)