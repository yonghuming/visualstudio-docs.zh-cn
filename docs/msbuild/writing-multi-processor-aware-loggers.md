---
title: "编写多处理器可识别的记录器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "记录器, 多处理器"
  - "msbuild, 可识别多处理器的记录器"
  - "多处理器记录器"
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 编写多处理器可识别的记录器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 利用多个处理器的能力可以缩短项目生成时间，但同时会增加生成事件日志记录的复杂性。  在单处理器环境下，事件、消息、警告和错误以可预测的顺序方式到达记录器。  但在多处理器环境下，来自不同源的事件可能同时或不按顺序到达。  为了应对此情况，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供了可以识别多处理器的记录器以及新的日志记录模型，并允许创建自定义“转发记录器”。  
  
## 多处理器日志记录面临的问题  
 在多处理器或多核系统中生成一个或多个项目时，将同时生成所有项目的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 生成事件。  大量事件消息可能会同时或不按顺序到达记录器。  由于 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 记录器并非为处理此情况而设计，因此这会严重影响记录器，并且会导致生成时间延长、记录器输出错误，甚至会导致生成中断。  为了解决这些问题，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 记录器可以处理顺序错误的事件并使事件与其源关联。  
  
 通过创建自定义转发记录器，可以更大程度地提高记录效率。  自定义转发记录器充当一个筛选器，允许您在生成前只选择要监视的事件。  使用自定义转发记录器时，不必要的事件不会严重影响记录器、造成日志混乱或降低生成速度。  
  
## 多处理器日志记录模型  
 为了应对与多处理器相关的生成问题，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支持两种日志记录模型：集中式和分布式。  
  
### 集中式日志记录模型  
 在集中式日志记录模型中，MSBuild.exe 的一个实例充当“中心节点”，该中心节点的子实例（“辅助节点）连接至中心节点，以帮助它执行生成任务。  
  
 ![中心记录器模型](~/msbuild/media/centralnode.png "CentralNode")  
  
 连接至中心节点的各种类型的记录器称为“中心记录器”。在同一时刻，每种记录器类型只能有一个实例可以连接到中心节点。  
  
 进行生成时，辅助节点会将其生成事件路由至中心节点。  中心节点会将其所有事件以及辅助节点的所有事件都路由至连接的一个或多个中心记录器。  然后，记录器便可创建基于传入数据的日志文件。  
  
 虽然只要求中心记录器实现 <xref:Microsoft.Build.Framework.ILogger>，但我们还建议您实现 <xref:Microsoft.Build.Framework.INodeLogger>，这样中心记录器便可用参与生成的节点数进行初始化。  引擎初始化记录器时，将调用 <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法的以下重载。  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 预先存在的任何基于 <xref:Microsoft.Build.Framework.ILogger> 的记录器都可以充当中心记录器，并可与生成连接。  但是，在对多处理器日志记录方案和顺序错误事件没有显式支持的情况下编写的中心记录器，可能会中断生成或产生无意义的输出。  
  
### 分布式日志记录模型  
 在集中式日志记录模型中，过多的传入消息通信量会严重影响中心节点，例如在同时生成许多项目时。  这样可能会对系统资源造成压力，并降低生成性能。  为了缓解此问题，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支持分布式日志记录模型。  
  
 ![分布式日志记录模型](~/msbuild/media/distnode.png "DistNode")  
  
 分布式日志记录模型允许用户创建转发记录器，从而对集中式日志记录模型进行了扩展。  
  
#### 转发记录器  
 转发记录器是一个辅助的轻量型记录器，它有一个事件筛选器连接至辅助节点，并从该节点接收传入的生成事件。  转发记录器对传入事件进行筛选，只将您指定的事件转发至中心节点。  这便减少了发送至中心节点的消息通信量，从而可以提高总体生成性能。  
  
 可通过以下两种方法来使用分布式日志记录：  
  
-   自定义名为 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 的预制转发记录器。  
  
-   编写您自己的自定义转发记录器。  
  
 可对 ConfigurableForwardingLogger 进行修改，以满足您的要求。  为此，请使用 MSBuild.exe 在命令行中调用记录器，并列出希望记录器转发至中心节点的生成事件。  
  
 或者，也可以创建自定义转发记录器。  通过创建自定义转发记录器，可以微调记录器的行为。  但是，创建自定义转发记录器比仅自定义 ConfigurableForwardingLogger 更复杂。  有关详细信息，请参阅[创建转发记录器](../msbuild/creating-forwarding-loggers.md)。  
  
## 将 ConfigurableForwardingLogger 用于简单分布式日志记录  
 若要连接 ConfigurableForwardingLogger 或自定义的转发记录器，请在 MSBuild.exe 命令行生成中使用 `/distributedlogger` 开关（缩写形式为 `/dl`）。  用于指定记录器类型名称和类的格式与 `/logger` 开关对应的格式相同，只是分布式记录器总是有两个而不是一个日志记录类：转发记录器和中心记录器。  下面是有关如何连接名为 XMLForwardingLogger 的自定义转发记录器的示例。  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  必须用星号 \(\*\) 来分隔 `/dl` 开关中的两个记录器名称。  
  
 使用 ConfigurableForwardingLogger 与使用其他任何记录器相似（如 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)中所述），区别在于要连接 ConfigurableForwardingLogger 记录器而不是通常的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 记录器，而且要将希望 ConfigurableForwardingLogger 传递到中心节点的事件指定为参数。  
  
 例如，如果只想在生成开始、结束以及发生错误时得到通知，则需将 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 作为参数来传递。  可以传递多个参数，参数之间用分号分隔。  下面是有关如何使用 ConfigurableForwardingLogger 只转发 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 事件的示例。  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 下面是可用的 ConfigurableForwardingLogger 参数的列表。  
  
|ConfigurableForwardingLogger 参数|  
|-------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|COMMANDLINE|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## 请参阅  
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)