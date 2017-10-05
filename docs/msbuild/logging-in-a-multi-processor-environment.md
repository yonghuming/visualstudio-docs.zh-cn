---
title: "多处理器环境中的日志记录 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e78d6c35fa294d2f1a39c91af5e278e9e4519d2d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="logging-in-a-multi-processor-environment"></a>多处理器环境下的日志记录
MSBuild 使用多个处理器的能力可以显著缩短项目生成时间，但同时会增加日志记录的复杂性。 在单处理器环境中，命令可以传入事件、 消息、 警告和错误可预测的顺序的方式处理记录器。 但是，在多处理器环境中，来自多个源的事件可以同时或不按顺序到达。 MSBuild 提供新的识别多处理器的记录器，并允许创建自定义"转发记录器。  
  
## <a name="logging-multiple-processor-builds"></a>日志记录多处理器生成  
 在多处理器或多核系统中生成一个或多个项目时，MSBuild 将同时生成所有项目的生成事件。 大量事件数据可能会在同一时间或不按顺序到达记录器。 这可以严重影响记录器，并会导致生成时间延长、 记录器输出错误或生成甚至中断。 若要解决这些问题，MSBuild 记录器可以处理乱序事件和关联事件和它们的源。  
  
 可提高通过创建自定义转发记录器更多的日志记录效率。 自定义转发记录器充当的筛选器通过让你选择，然后构建，你想要监视的事件。 当你使用自定义转发记录器时，不必要的事件执行不严重影响记录器、 造成日志，混乱或降低生成速度。  
  
### <a name="central-logging-model"></a>集中式日志记录模型  
 对于多处理器生成，MSBuild 将使用"集中式日志记录模型"。 集中式日志记录模型中的 MSBuild.exe 实例充当主生成过程中或"中央节点。 MSBuild.exe 或"辅助节点，"的辅助实例附加到中心节点。 连接到中央节点任何基于 ILogger 记录器也称为"中央记录器"并连接到辅助节点的记录器都称为"辅助记录器。  
  
 进行生成时，辅助记录器将其事件流量路由到中心记录器。 因为事件来源在多个辅助节点，此数据将同时到达中心节点，但交错。 若要解析到项目中事件和事件目标的引用，事件自变量包含其他生成事件上下文信息。  
  
 尽管仅<xref:Microsoft.Build.Framework.ILogger>是需要由中心记录器实现，我们建议你实现<xref:Microsoft.Build.Framework.INodeLogger>如果你想要参与生成的节点数的初始化的中央记录器。 以下重载<xref:Microsoft.Build.Framework.ILogger.Initialize%2A>引擎初始化记录器时均会调用方法：  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>分布式日志记录模型  
 在集中式日志记录模型中，过多传入的消息通信量，如多个项目进行生成时，会占用大量的中心节点，从而强调系统，同时降低生成性能。  
  
 为了减少这个问题，MSBuild 还提供了"分布式日志记录模型"，它通过让你创建转发记录器扩展集中式日志记录模型。 转发记录器附加到辅助节点，并从该节点接收传入的生成事件。 转发记录器就如同正则记录器，只不过它可以筛选的事件，且然后将转发仅到中央节点所需的。 这样可以减少中心节点上的消息通信量，并因此可以更好的性能。  
  
 你可以通过实现创建转发记录器<xref:Microsoft.Build.Framework.IForwardingLogger>接口，派生自<xref:Microsoft.Build.Framework.ILogger>。 接口如下定义：  
  
```csharp
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 若要将转发转发记录器中的事件，调用<xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A>方法<xref:Microsoft.Build.Framework.IEventRedirector>接口。 传递相应<xref:Microsoft.Build.Framework.BuildEventArgs>，或作为参数的派生。  
  
 有关详细信息，请参阅[创建转发记录器](../msbuild/creating-forwarding-loggers.md)。  
  
### <a name="attaching-a-distributed-logger"></a>连接分布式的记录器  
 附加命令行生成一个分布式的记录器，请使用`/distributedlogger`(或，`/dl`简称) 切换。 指定的记录器类型和类名称的格式都是相同的`/logger`切换，只不过是分布式的记录器组成两个日志记录类： 转发记录器和中心记录器。 以下是连接分布式的记录器的示例：  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 星号 （*） 用于分隔中的两个记录器名称`/dl`切换。  
  
## <a name="see-also"></a>另请参阅  
 [生成记录器](../msbuild/build-loggers.md)   
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)
