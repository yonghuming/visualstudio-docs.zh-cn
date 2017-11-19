---
title: "自动功能挂起 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: a2c836364092aa71f40d4d7aa4566b2d12def00e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-feature-suspension"></a>自动功能挂起
如果你的可用系统内存降到 200 MB 或更少，Visual Studio 将在代码编辑器中显示以下消息。  
  
 ![警报文本中挂起完整解决方案分析](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 当 Visual Studio 检测到内存不足的情况时，自动暂停，某些高级的功能，以帮助其保持不变。 当此高级功能挂起警告将出现，Visual Studio 将继续像以前那样工作，但其性能将会略有下降。  
  
 在内存不足情况下，将发生以下情况：  
  
-   对于 Visual C# 和 Visual Basic 的完整解决方案分析处于禁用状态。  
  
-   [垃圾回收](/dotnet/standard/garbage-collection/index)(GC) Visual C# 和 Visual Basic 的低延迟模式已禁用。  
  
-   Visual Studio 将缓存刷新。  
  
## <a name="improve-visual-studio-performance"></a>提高 Visual Studio 性能  
 提示和技巧有关如何改进 Visual Studio 性能处理大型解决方案或内存不足情况时，请参阅[针对大型解决方案的性能注意事项](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。  
  
## <a name="full-solution-analysis-suspended"></a>挂起的完整解决方案分析  
 默认情况下，完整解决方案分析适用于 Visual Basic 启用和禁用对于 Visual C#。 但是，在内存不足情况下，完整解决方案分析会自动禁用 Visual Basic 和 Visual C#，而不考虑其设置选项对话框中。 但是，你可以重新启用完整解决方案分析通过选择**重新启用**中的信息栏中出现时，通过选择按钮**启用完整解决方案分析**复选框，在选项对话框中，或通过重新启动 Visual Studio。 选项对话框中始终显示当前的完整解决方案分析设置。 有关详细信息，请参阅[如何： 启用和禁用完整解决方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)。  
  
## <a name="gc-low-latency-disabled"></a>禁用 GC 低延迟  
 若要重新启用 GC 低延迟模式，重新启动 Visual Studio。  默认情况下，Visual Studio 启用 GC 低延迟模式，只要您键入以确保您键入的内容不会阻止任何 GC 操作。 但是，如果内存不足的情况导致 Visual Studio 显示自动挂起警告，GC 低延迟模式会禁用该会话中。 重新启动 Visual Studio 将重新启用默认 GC 行为。 有关详细信息，请参阅[GCLatencyMode 枚举](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87)。  
  
## <a name="visual-studio-caches-flushed"></a>Visual Studio 缓存刷新  
 Visual Studio 的所有缓存将立即清空，但将开始重新填充如果继续你当前的开发会话或重新启动 Visual Studio。 刷新的缓存包括以下功能的缓存。  
  
-   查找所有引用  
  
-   定位到  
  
-   添加 Using  
  
 此外，用于内部 Visual Studio 操作的缓存也将被清除。  
  
> [!NOTE]
>  自动功能挂起警告只出现一次是每个会话为基础的每个解决方案基础上。 这意味着，如果你从 Visual Basic 切换到 Visual C# （或相反），并运行到另一个内存不足的情况，你可能可以获得另一个自动功能挂起警告。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 启用和禁用完整解决方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [垃圾回收的基础](/dotnet/standard/garbage-collection/fundamentals)   
 [针对大型解决方案的性能注意事项](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)