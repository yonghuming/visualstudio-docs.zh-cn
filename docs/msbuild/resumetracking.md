---
title: "ResumeTracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

恢复当前上下文中的跟踪。  
  
## 语法  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## 返回值  
 恢复跟踪时，带 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位组的 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  如果由于上下文不可用而不能恢复跟踪，则返回 [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True)。  
  
## 要求  
 **Header:** FileTracker.h  
  
## 请参阅  
 [SuspendTracking](../msbuild/suspendtracking.md)