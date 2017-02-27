---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定根标记使用响应文件启动跟踪上下文。  
  
## 语法  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### 参数  
 \[in\] `intermediateDirectory`  
 要将跟踪日志存储到的目录。  
  
 \[in\] `taskName`  
 识别跟踪上下文。  名称用于创建日志文件名称。  
  
 \[in\] `rootMarkerResponseFile`  
 包含根标记的响应文件的路径名。  根名称用于将所有上下文跟踪组合在一起。  
  
## 返回值  
 如果创建了跟踪上下文，则设置一个具有 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位的 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 要求  
 **Header:** FileTracker.h  
  
## 请参阅  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)