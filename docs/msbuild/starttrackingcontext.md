---
title: "StartTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

启动跟踪上下文。  
  
## 语法  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### 参数  
 \[in\] `intermediateDirectory`  
 要将跟踪日志存储到的目录。  
  
 \[in\] `taskName`  
 识别跟踪上下文。  名称用于创建日志文件名称。  
  
## 返回值  
 如果创建了跟踪上下文，则设置一个具有 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位的 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 要求  
 **Header:** FileTracker.h