---
title: "多处理器环境下的日志记录 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 日志记录"
  - "MSBuild, 多处理器日志记录"
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 多处理器环境下的日志记录
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild使用多个处理器的能力可以显著缩短项目生成时间，但同时会增加日志记录的复杂性。  在单处理器环境下，记录器通过可预测的顺序方式来处理传入的事件、消息、警告和错误。  但在多处理器环境下，来自多个源的事件可能同时或不按顺序到达。  MSBuild提供了可以识别多处理器的新记录器，并允许创建自定义“转发记录器”。  
  
## 记录多处理器生成  
 在多处理器或多核系统中生成一个或多个项目时，MSBuild将同步生成所有项目的生成事件。  大量事件数据可能会同时或不按顺序到达记录器。  这会严重影响记录器以及导致生成时间延长、记录器输出错误，甚至会导致生成中断。  为了解决这些问题，MSBuild记录器可以处理顺序错误的事件并使事件与其源关联。  
  
 通过创建自定义转发记录器，可以更大程度地提高记录效率。  自定义转发记录器充当一个筛选器，允许您在生成前选择要监视的事件。  使用自定义转发记录器时，不必要的事件不会严重影响记录器、造成日志混乱或降低生成速度。  
  
### 集中式日志记录模型  
 对于多处理器生成，MSBuild 使用“集中式日志记录模型”。在集中式日志记录模型中，MSBuild.exe 的实例用作主生成进程或“中心节点”。MSBuild.exe 的辅助实例或“辅助节点”连接至中心节点。  连接到中心节点的任何基于 ILogger 的记录器都称为“中心记录器”，连接到辅助节点的记录器则称为“辅助记录器”。  
  
 进行生成时，辅助记录器会将其事件通信路由至中心记录器。  由于事件源自多个辅助节点，因此数据同时但交错到达中心节点。  为了解决事件到项目和事件到目标引用，事件参数包含其他生成事件上下文信息。  
  
 尽管只要求中心记录器实现 <xref:Microsoft.Build.Framework.ILogger>，但如果希望中心记录器用参与生成的节点数进行初始化，则建议您同时也要实现 <xref:Microsoft.Build.Framework.INodeLogger>。  引擎初始化记录器时，将调用 <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法的以下重载：  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### 分布式日志记录模型  
 在集中式日志记录模型中，过多的传入消息通信量（例如在一次生成许多项目时）会严重影响中心节点，从而对系统造成过大压力，并降低生成性能。  
  
 为了减少此问题，MSBuild 还启用了“分布式日志记录模型”，该模型通过允许用户创建转发记录器来扩展集中式日志记录模型。  转发记录器连接至辅助节点，并从该节点接收传入的生成事件。  转发记录器与常规记录器基本相同，只是转发记录器可以筛选事件，然后只将所需事件转发至中心节点。  这便减少了中心节点处的消息通信量，因此可以改善性能。  
  
 通过实现派生自 <xref:Microsoft.Build.Framework.ILogger> 的 <xref:Microsoft.Build.Framework.IForwardingLogger> 接口可以创建转发记录器。  该接口定义为：  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 若要在转发记录器中转发事件，请调用 <xref:Microsoft.Build.Framework.IEventRedirector> 接口的 <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> 方法。  将相应的 <xref:Microsoft.Build.Framework.BuildEventArgs> 或派生作为参数传递。  
  
 有关详细信息，请参阅[创建转发记录器](../msbuild/creating-forwarding-loggers.md)。  
  
### 连接分布式记录器  
 若要在命令行生成中连接分布式记录器，请使用 `/distributedlogger`（或缩写形式 `/dl`）开关。  用于指定记录器类型名称和类的格式与 `/logger` 开关对应的格式相同，只是分布式记录器由两个日志记录类构成：一个转发记录器和一个中心记录器。  下面是连接分布式记录器的一个示例：  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 星号 \(\*\) 用于分隔 `/dl` 开关中的两个记录器名称。  
  
## 请参阅  
 [生成记录器](../msbuild/build-loggers.md)   
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)