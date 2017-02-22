---
title: "marker_series 类 | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series 类"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series 类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示单个提供程序生成的事件的序列通道。  
  
## 语法  
  
```  
class marker_series;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[marker\_series::marker\_series 构造函数](../Topic/marker_series::marker_series%20Constructor.md)|初始化 `marker_series` 类的新实例。|  
|[marker\_series::~marker\_series 析构函数](../profiling/marker-series-tilde-marker-series-destructor.md)|销毁 marker\_series 对象并且释放所有已分配的资源。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[marker\_series::is\_enabled 方法](../Topic/marker_series::is_enabled%20Method.md)|确定会话是否启用任何提供程序。|  
|[marker\_series::write\_alert 方法](../profiling/marker-series-write-alert-method.md)|将警报写入并发可视化工具跟踪文件。|  
|[marker\_series::write\_flag 方法](../profiling/marker-series-write-flag-method.md)|将标志写入并发可视化工具跟踪文件。|  
|[marker\_series::write\_message 方法](../profiling/marker-series-write-message-method.md)|将消息写入并发可视化工具跟踪文件。|  
  
## 继承层次结构  
 `marker_series`  
  
## 要求  
 **页眉：**cvmarkersobj.h  
  
 **命名空间:** Concurrency::diagnostic。  
  
## 请参阅  
 [diagnostic 命名空间](../profiling/diagnostic-namespace.md)