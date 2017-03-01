---
title: "适用于语言的重要命令服务筛选器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6b5bad11c47074c29f3b319678419f1e42ab91b
ms.lasthandoff: 02/22/2017

---
# <a name="important-commands-for-language-service-filters"></a>重要的语言服务筛选器的命令
如果你想要创建一个全功能的语言服务筛选器，请考虑处理下面的命令。 在中定义的命令标识符的完整列表<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>枚举为托管的代码和 Stdidcmd.h 标头文件对于非托管[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]代码。</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 您可以找到 Stdidcmd.h 文件*Visual Studio SDK 安装路径*\VisualStudioIntegration\Common\Inc。  
  
## <a name="commands-to-handle"></a>对句柄的命令  
  
> [!NOTE]
>  不强制要求，以针对下表中的每个命令进行筛选。  
  
|命令|说明|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户右键单击发送。 此命令指示它是时间来提供的快捷菜单。 如果不处理此命令，文本编辑器将提供默认的快捷菜单，而无需任何特定于语言的命令。 若要包含在此菜单上的命令，处理命令并自行显示的快捷菜单。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常，在用户键入 CTRL + J 时发送。 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>显示语句完成框。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入字符时发送。 监视此命令，以确定当键入触发器字符并要提供语句完成、 方法提示和文本的标记，如语法着色，大括号匹配，以及错误的标记。 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>语句结束和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>方法提示和技巧。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 若要支持文本标记，监视此命令，以确定键入的字符是否需要更新您的标记。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入 Enter 键时发送。 监视此命令，以确定何时关闭方法提示窗口，通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 默认情况下，在文本视图处理此命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户键入 Backspace 键时发送。 监视以确定何时通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>，则关闭方法提示窗口 默认情况下，在文本视图处理此命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|从菜单或快捷键发送。 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>若要使用的参数信息更新提示窗口中。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|当用户悬停在变量上或将光标放置在变量上，选择时，发送**快速信息**从**IntelliSense**中**编辑**菜单。 通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法的时间为<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>提示中返回变量的类型 如果调试处于活动状态，该提示还应显示该变量的值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常，当用户键入 CTRL + 空格键时发送。 此命令指示要调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>的时间为<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>的语言服务|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|从菜单中，通常发送**注释所选内容**或**取消注释选定内容**从**高级**中**编辑**菜单。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指示用户想要注释掉所选的文本;<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指示用户是否要取消注释所选的文本。</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 这些命令可以实现只能由语言服务。|  
  
## <a name="see-also"></a>另请参阅  
 [开发旧语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)
