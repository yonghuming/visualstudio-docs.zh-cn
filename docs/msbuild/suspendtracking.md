---
title: "SuspendTracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SuspendTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SuspendTracking"
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# SuspendTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

挂起当前上下文中的跟踪。  
  
## 语法  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## 返回值  
 挂起跟踪时，带 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位组的 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 要求  
 **Header:** FileTracker.h  
  
## 请参阅  
 [ResumeTracking](../msbuild/resumetracking.md)