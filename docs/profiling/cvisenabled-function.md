---
title: "CvIsEnabled 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled 方法"
  - "CvIsEnabledEx 方法"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvIsEnabled 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

确定某个会话是否已启用指定的 ETW 提供程序标记。  
  
## 语法  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### 参数  
 `category`  
 分类  
  
 `level`  
 重要程度。  
  
 `pProvider`  
 有效的提供程序对象。  不能为 NULL。  
  
## 返回值  
 S\_OK，如果提供程序当前已启用。  S\_FALSE，如果提供程序当前禁用。  错误代码，当有任何错误时。  使用 FAILED 宏检查错误状态然后检查 S\_OK\/S\_FALSE。  
  
## 要求  
 **页眉：**cvmarkers.h  
  
## 请参阅  
 [C\+\+ 库参考](../profiling/cpp-library-reference.md)