---
title: "WriteContextTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

写入日志文件用于当前上下文。  
  
## 语法  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### 参数  
 \[in\] `intermediateDirectory`  
 要将跟踪日志存储到的目录。  
  
 \[in\] `tlogRootName`  
 日志文件名的根名称。  
  
## 返回值  
 如果创建了跟踪上下文，则设置一个具有 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位的 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 要求  
 **Header:** FileTracker.h  
  
## 请参阅  
 [WriteAllTLogs](../msbuild/writealltlogs.md)