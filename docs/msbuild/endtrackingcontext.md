---
title: "EndTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "EndTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "EndTrackingContext"
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# EndTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

结束当前跟踪上下文  
  
## 语法  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## 返回值  
 结束跟踪上下文时，带 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) 位组的 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)。  
  
## 要求  
 **Header:** FileTracker.h  
  
## 请参阅  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)