---
title: "VsgDbg::~VsgDbg（析构函数） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg（析构函数）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

销毁 `VsgDbg` 类的实例。  如果图形信息正在被记录，绘图日志文件定稿和关闭，同时积极捕捉图像信息所用的所有资源被释放。  
  
## 语法  
  
```cpp  
~VsgDbg();  
```  
  
## 请参阅  
 [VsgDbg::VsgDbg（构造函数）](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)