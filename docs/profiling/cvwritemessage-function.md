---
title: "CvWriteMessage 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteMessageW"
  - "cvmarkers/CvWriteMessageExW"
  - "cvmarkers/CvWriteMessageVA"
  - "cvmarkers/CvWriteMessageExVW"
  - "cvmarkers/CvWriteMessageExA"
  - "cvmarkers/CvWriteMessageA"
  - "cvmarkers/CvWriteMessageExVA"
  - "cvmarkers/CvWriteMessageVW"
helpviewer_keywords: 
  - "CvWriteMessageExVA 方法"
  - "CvWriteMessageW 方法"
  - "CvWriteMessageVW 方法"
  - "CvWriteMessageExVW 方法"
  - "CvWriteMessageExW 方法"
  - "CvWriteMessageA 方法"
  - "CvWriteMessageVA 方法"
  - "CvWriteMessageExA 方法"
ms.assetid: e20ae7be-bfa7-437a-b8c1-fa0f1baa7f83
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# <a name="cvwritemessage-function"></a>CvWriteMessage 函数
向并发可视化工具跟踪文件写入一条消息。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CvWriteMessageW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageA(  
    PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>参数  
 `argList`  
 参数列表。  
  
 `category`  
 范围的类别  
  
 `level`  
 范围的重要性级别。  
  
 `pMarkerSeries`  
 有效标记系列上下文。 不能为 NULL。  
  
 `pMessage`  
 消息格式字符串。 不能为 NULL。  
  
## <a name="return-value"></a>返回值  
 成功写入消息时返回 S_OK。 出现任何错误时返回错误代码。 使用 SUCCEEDED/FAILED 宏检查错误条件。  
  
## <a name="requirements"></a>要求  
 **标头：**cvmarkers.h  
  
 **Unicode：**CvWriteMessageW、CvWriteMessageVW、CvWriteMessageExW、CvWriteMessageExVW  
  
 **ANSI：**CvWriteMessageA、CvWriteMessageVA、CvWriteMessageExA、CvWriteMessageExVA  
  
## <a name="see-also"></a>另请参阅  
 [C++ 库参考](../profiling/cpp-library-reference.md)


<!--HONumber=Feb17_HO4-->


