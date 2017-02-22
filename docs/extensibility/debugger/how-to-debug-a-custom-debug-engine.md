---
title: "如何: 调试自定义调试引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎调试"
  - "调试 [调试 SDK]，自定义调试引擎"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 调试自定义调试引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项类型从生成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 方法的调试引擎 \(DE\)。  这意味着、生成由控制项类型的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的控件实例。  但是， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 该实例不能调试 DE。  哪些操作。允许您的步骤调试该自定义 DE。  
  
> [!NOTE]
>  :   在 “自定义调试引擎”程序的调试，必须等待 DE 开始，您可以附加到它。  如果您在出现 DE 的开头的放置一个消息框时、开始，您可以在然后附加清除继续的消息框。  这样，您可以捕捉所有 DE 事件。  
  
> [!WARNING]
>  ，然后再尝试以下过程之前，您必须具有远程调试安装。  有关详细信息，请参见[远程调试](../../debugger/remote-debugging.md)。  
  
### 调试自定义调试引擎  
  
1.  启动 msvsmon.exe，远程调试监视器。  
  
2.  在 msvsmon.exe 的 **工具** 菜单中，选择 **选项** 打开 **选项** 对话框。  
  
3.  选择 “无身份验证”选项并单击 **好**。  
  
4.  开始 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 实例并打开自定义、 project。  
  
5.  开始 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 第二个实例并打开生成 DE 的自定义项 \(用于开发，这通常在的设置实验注册表项，即使安装 VSIP\)。  
  
6.  在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]第二个实例，从该自定义项中加载一个源文件并启动程序要调试。  请等待几个时间允许 DE 填充或等待，直到命中断点。  
  
7.  首先 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(带有、 project\)，从 **调试** 菜单中选择 **附加的进程** 。  
  
8.  在 **附加的进程** 对话框中，将 **传输** 到 **远程 \(仅限本机无身份验证\)**。  
  
9. 更改 **限定符** 到设备 \(请注意的名称:具有项的历史记录，因此，您需要一次只输入此名称\)。  
  
10. 在 **可用进程** 列表中，选择运行 DE 的实例并单击 **附加** 按钮。  
  
11. 在符号在 DE 后加载之后，将断点在 DE 代码。  
  
12. 在停止并重新启动调试进程时，重复步骤 6 至步骤。  
  
### 调试自定义项类型  
  
1.  在正常注册表项的开始 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 和加载项目类型的项 \(这是，对项目类型的源，而不是实例化项类型\)。  
  
2.  打开项目属性并转到 **调试** 页。  对于 **命令**，键入路径。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE \(默认情况下，这是 *\[drivers\]*\\Program Files\\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8 \\Common7\\IDE \\ devenv.exe。\)  
  
3.  为 **命令参数**，实验注册表项的类型 `/rootsuffix exp` \(创建在安装了 VSIP\)。  
  
4.  单击**“确定”**接受更改。  
  
5.  按 F5 启动项目类型。  这将生成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]第二个实例。  
  
6.  此时，您可以在项目类型源代码中设置断点。  
  
7.  在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]第二个实例，则加载或创建项类型的新实例。  在加载或创建时，断点可能会命中。  
  
8.  调试项目类型。  
  
9. 如果选择调试生成、处理，可以在 “自定义调试引擎”过程执行中的步骤附加到 DE 的调试，则在生成后。  这将为您提供了三实例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 运行:实例化的项目类型的项类型的源、一个和第三个附加到 DE。  
  
## 请参阅  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)