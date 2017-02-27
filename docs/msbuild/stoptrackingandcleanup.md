---
title: "StopTrackingAndCleanup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

停止所有跟踪并释放所有跟踪会话所使用的内存。  
  
## 语法  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## 返回值  
 如果跟踪停止，返回 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)，同时设置了 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位。  
  
## 要求  
 **Header:** FileTracker.h  
  
## 请参阅  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)