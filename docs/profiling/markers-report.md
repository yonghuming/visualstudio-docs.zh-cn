---
title: "标记报告 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9d546e96d92c26725bc8a169c413bc7b96feb7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="markers-report"></a>标记报告
标记报告列出所显示时间范围内的标记。  平移、缩放或隐藏通道，可能会导致标记显示或消失。 报告中包含有关各个标记的以下信息：  
  
-   开始时间，相对于跟踪的开始时间。  
  
-   持续时间。 标志和消息代表瞬时，因此它们的持续时间为零。  
  
-   生成标记的线程的 ID。  
  
-   生成标记的 Windows 事件跟踪 (ETW) 提供程序。  
  
-   从中写入标记的标记序列。  
  
-   标记所属的事件类别。  
  
-   标记的重要性级别。  
  
-   标记的类型（范围、标志或消息）。  
  
-   有关标记所代表的内容的简略说明。  
  
 选择“导出”按钮，将标记报告保存为 CSV 文件。 可以将 CSV 文件中的数据与其他应用或工具一起使用。  
  
> [!NOTE]
>  标记报告可显示 1,000 个标记。 若要查看全部标记，请将整个报告导出到 CSV 文件。