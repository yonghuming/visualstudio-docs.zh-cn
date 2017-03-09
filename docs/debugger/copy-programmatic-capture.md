---
title: "复制（编程捕获） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 复制（编程捕获）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

复制有效的图像记录 \(.vsglog\) 文件的内容到新文件。  
  
## 语法  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### 参数  
 `szNewVSGLog`  
 新图像日志文件的文件名。  
  
## 备注  
 若要复制图像信息到新文件，您必须已经捕获一些图形信息；否则，则不会执行任何操作。