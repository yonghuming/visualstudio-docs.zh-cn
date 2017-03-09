---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

完成图像日志文件，将其关闭，并且当 app 用来跟踪图像信息时释放使用的资源。  
  
## 语法  
  
```cpp  
void UnInit();  
```  
  
## 备注  
 当 `VsgDbg` 类的实例被销毁时，`UnInit` 被自动调用。  如果 `VsgDbg` 实例不是记录图像信息，这也没影响。  
  
 在 `UnInit` 调用一个 `VsgDbg` 类实例后，一个新的图像日志文件通过调用 `Init` 和 `UnInit` 被创建。  你可以重复使用同一个 `VsgDbg` 实例来创建几个独立的图像日志文件。  
  
## 请参阅  
 [Init](../debugger/init.md)