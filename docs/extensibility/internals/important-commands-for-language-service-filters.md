---
title: "有关语言的重要命令服务筛选器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c0fa4b408c43acbf2ec87bcfaca5135c9037af7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="important-commands-for-language-service-filters"></a>语言服务筛选器的重要命令
如果你想要创建一个功能完整的语言服务筛选器，请考虑处理以下命令。 在中定义的命令标识符的完整列表<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>枚举为托管的代码和 Stdidcmd.h 标头文件对于非托管[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]代码。 你可以找到 Stdidcmd.h 文件*Visual Studio SDK 安装路径*\VisualStudioIntegration\Common\Inc。  
  
## <a name="commands-to-handle"></a>到句柄的命令  
  
> [!NOTE]
>  它并不一定要针对下表中的每个命令的筛选器。  
  
|命令|描述|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户单击鼠标右键时发送。 此命令指示它是时间来提供快捷菜单。 如果不处理此命令，文本编辑器将提供默认的快捷菜单，而无需任何特定于语言的命令。 若要包含在此菜单上的命令，处理命令并自行显示的快捷菜单。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入 CTRL + J 通常发送。 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>显示语句完成框。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入字符时发送。 监视此命令，以确定何时键入触发器字符，并提供语句完成、 方法提示和文本标记，如语法着色、 大括号匹配，以及错误的标记。 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>语句完成和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>方法的提示和技巧。 若要支持文本标记，监视此命令，以确定键入的字符是否需要更新你的标记。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入 Enter 键时发送。 监视此命令，以确定何时调用解除方法提示窗口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。 默认情况下，文本视图处理此命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入 Backspace 键时发送。 监视器以确定何时调用解除方法提示窗口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。 默认情况下，文本视图处理此命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|从菜单或快捷键发送。 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>若要使用的参数信息更新提示窗口。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户悬停在变量上或将光标置于的变量上，选择时，发送**快速信息**从**IntelliSense**中**编辑**菜单。 返回一条提示中的变量的类型，通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。 如果调试处于活动状态，提示应还显示变量的值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入 CTRL + 空格键时，通常发送。 此命令将指示语言服务调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|从菜单中，通常发送**注释选定内容**或**取消注释所选内容**从**高级**中**编辑**菜单。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指示用户想要注释掉所选的文本;<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指示用户想要取消注释所选的文本。 这些命令可以仅由语言服务实现。|  
  
## <a name="see-also"></a>另请参阅  
 [开发旧版语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)