---
title: "将 EventSource 事件作为标记可视化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 将 EventSource 事件作为标记可视化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

并发可视化工具可将的 EventSource 事件显示为标记，并且可以控制标记如何显示。  若要查看 EventSource 标记，通过使用 [高级设置](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 对话框，注册 ETW 提供程序 GUID。  并发可视化工具默认约定表示 EventSource 事件为 [标志标记](../profiling/flag-markers.md), [范围标记](../profiling/span-markers.md), 和 [消息标记](../profiling/message-markers.md).  您可以自定义 EventSource 事件如何通过添加自定义字段到事件显示。  有关标记的更多信息，请参见[并发可视化工具标记](../profiling/concurrency-visualizer-markers.md)。  有关 EventSource 事件的更多信息，请参见 <xref:System.Diagnostics.Tracing>。  
  
## 默认 EventSource 事件的可视化效果  
 默认情况下，并发可视化工具使用下列约定表示 EventSource 事件。  
  
### 标记类型  
  
1.  具有 [Opcode](http://msdn.microsoft.com/zh-cn/d97953df-669b-4c55-b1a8-925022b339b7) 胜利的事件：开始或胜利：开头或结尾跨度被视为停止。嵌套或重叠范围无法显示。  在一个线程开始和在另一个结束将事件对无法显示。  
  
2.  Opcode 不是 win:Start 和 win:Stop 的事件将标记标志，除非其 [级别](http://msdn.microsoft.com/zh-cn/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR 字段\) 是胜利：详细的或更高版本。  
  
3.  在所有其他情况下，事件被处理为消息。  
  
### 重要性  
 下表定义如何将事件级别映射为标记重要性。  
  
|ETW 级别|并发可视化工具重要性|  
|------------|----------------|  
|win:LogAlways|Normal|  
|win:Critical|Critical|  
|win:Error|Critical|  
|win:Warning|高|  
|win:Informationa （信息性）|Normal|  
|win:Verbose|低|  
|大于 win:verbose|低|  
  
### 序列名称。  
 用于系列名称的事件中的任务名称。  如果事件尚未定义任务，系列命名为空。  
  
### 类别  
 如果级别是 win:Critical 或 win:Error，则类别是提醒 \(\-1\)。  否则，类别默认是 \(0\)。  
  
### Text  
 如果 printf 格式类型文本消息为事件定义，它显示为标记的说明。  否则，是描述为事件的名称和每个负载字段值。  
  
## 自定义 EventSource 的可视化效果事件  
 您可以自定义 EventSource 事件如何通过将适当的字段显示为事件，如下节所述。  
  
### 标记类型  
 使用 `cvType` 字段，一个字节，控制表示的此事件标记。  此处有适用于 cvType 的值：  
  
|cvType 值|产生标记类型|  
|--------------|------------|  
|0|消息|  
|1|跨度开始|  
|2|跨度末尾|  
|3|Flag|  
|所有其他值|消息|  
  
### 重要性  
 可以使用 `cvImportance` 字段，一个字节，控制 EventSource 事件的重要性设置。  但是，我们建议使用它的级别控制事件的重要性。  
  
|cvImportance 值|并发可视化工具重要性|  
|--------------------|----------------|  
|0|Normal|  
|1|Critical|  
|2|高|  
|3|高|  
|4|Normal|  
|5|低|  
|所有其他值|低|  
  
### 序列名称。  
 使用 `cvSeries` 事件字段 ，一个字符串，控制并发可视化工具为 EventSource 事件提供的的一系列名称。  
  
### 类别  
 使用 `cvCategory` 字段，一个字节，控制并发可视化工具为 EventSource 事件提供的类别。  
  
### Text  
 使用 `cvTextW` 字段，一个字符串，控制并发可视化工具为 EventSource 事件提供的说明。  
  
### SpanID  
 使用 cvSpanId 字段，int，与事件匹配成对。  表示跨度的每对值启动\/停止事件必须是唯一的。  通常对于并发代码，这需要使用同步基元例如 <xref:System.Threading.Interlocked.Exchange%2A> 来确保（用于 CvSpanID 的值）值是正确的。  
  
> [!NOTE]
>  将 SpanID 用于嵌套跨度，允许它们对同一线程部分重叠或允许它们从一个线程开始，而从另一个不受支持的线程结束。  
  
## 请参阅  
 [并发可视化工具标记](../profiling/concurrency-visualizer-markers.md)