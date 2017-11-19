---
title: "如何： 调试自定义调试引擎 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a91dbb7797d69ec71b776eeef5e34e0ced21ad9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-custom-debug-engine"></a>如何： 调试自定义调试引擎
项目类型中启动的调试引擎 (DE)<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法。 这意味着 DE 启动的实例的控制之下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]控制项目类型。 但是，该实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]无法调试 DE。 下面是可用于调试自定义 DE 的步骤。  
  
> [!NOTE]
>  ： 在"调试自定义调试引擎"过程中，你必须等待 DE 启动之前可以将附加到它。 如果 DE 启动时显示你 DE 开头放置一个消息框，你可以附加在该点，然后清除该消息框以继续。 这样一来，你可以捕获所有 DE 事件。  
  
> [!WARNING]
>  你必须具有远程调试安装，然后尝试以下过程。 请参阅[远程调试](../../debugger/remote-debugging.md)有关详细信息。  
  
### <a name="debugging-a-custom-debug-engine"></a>调试自定义调试引擎  
  
1.  启动 msvsmon.exe，远程调试监视器。  
  
2.  从**工具**菜单中选择 msvsmon.exe**选项**以打开**选项**对话框。  
  
3.  选择"无身份验证"选项并单击**确定**。  
  
4.  启动的实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]并打开自定义 DE 项目。  
  
5.  启动第二个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]并打开启动 DE 你自定义项目 （对于开发，这通常是在安装 VSIP 时设置的实验性注册表配置单元中）。  
  
6.  此第二个实例中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 从自定义项目加载源文件和启动要调试程序。 请稍等片刻以允许 DE 加载，或等待，直到命中断点。  
  
7.  中的第一个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（与 DE 项目），选择**附加到进程**从**调试**菜单。  
  
8.  在**附加到进程**对话框中，更改**传输**到**远程 （无身份验证时仅限本机）**。  
  
9. 更改**限定符**为您的计算机的名称 (请注意： 没有历史记录的条目，因此你需要键入中此名称仅一次)。  
  
10. 在**可用进程**列表中，选择正在运行，并单击你 DE 实例**附加**按钮。  
  
11. 在你 DE 中已加载符号后，请在 DE 代码中设置断点。  
  
12. 每次你停止并重新启动调试进程，重复步骤 6 至 10。  
  
### <a name="debugging-a-custom-project-type"></a>调试自定义项目类型  
  
1.  启动[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]正常注册表配置单元和负载中你的项目类型 （这是，将源与你的项目类型，不你的项目类型的实例化） 的项目。  
  
2.  打开项目属性并转到**调试**页。 有关**命令**，键入的路径[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (默认情况下，这是*[驱动器]*files\microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe)。  
  
3.  有关**命令参数**，类型`/rootsuffix exp`实验注册表配置单元 （VSIP 安装时创建）。  
  
4.  单击“确定”  接受这些更改。  
  
5.  按 F5 启动你的项目类型。 这将启动的第二个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
6.  此时，你可以在你项目类型的源代码中设置断点。  
  
7.  中的第二个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 加载或创建你的项目类型的新实例。 在加载或创建时，可能会命中断点。  
  
8.  调试你的项目类型。  
  
9. 如果你选择调试启动 DE 的过程，你可以将它启动后附加到你 DE 的"调试自定义调试引擎"步骤中执行的步骤。 这将为你提供的三个实例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]运行： 一个用于您的项目类型源、 附加到你 DE 第三个您实例化的项目类型，以及第二个。  
  
## <a name="see-also"></a>另请参阅  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)