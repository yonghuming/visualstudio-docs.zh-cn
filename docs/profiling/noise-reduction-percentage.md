---
title: "降噪百分比 | Microsoft Docs"
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
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "并发可视化工具, 降噪百分比"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 降噪百分比
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

默认情况下，降噪百分比设置的值为 2。  调用树中只显示其非独占时间百分比大于或等于此设置的项。  通过更改此设置，您可以控制在调用树中显示的项数。  例如，如果将此值更改为 10，将只显示其非独占时间百分比大于或等于 10% 的调用树项。  通过增大此设置的值，您可以关注对进程性能影响较大的项。