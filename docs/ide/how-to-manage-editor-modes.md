---
title: "如何：管理编辑器模式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 71566f11a069d266ded2aebe02bbf388cf00730e
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-editor-modes"></a>如何：管理编辑器模式
可在各种显示模式下显示 Visual Studio 代码编辑器。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="enabling-full-screen-mode"></a>启用全屏模式  
 启用“全屏”模式后，可选择隐藏所有工具窗口并仅查看文档窗口。  
  
#### <a name="to-enable-full-screen-mode"></a>启用全屏模式  
  
-   按 Alt+Shift+Enter 可进入或退出“全屏”。  
  
     --或者--  
  
-   在“命令”窗口中发出命令 `View.Fullscreen`。  
  
## <a name="enabling-virtual-space-mode"></a>启用虚空格模式  
 在“虚空格”模式下，将在每个代码行末尾插入空格。 选择此选项可将注释放置在代码旁的一致位置。  
  
#### <a name="to-enable-virtual-space-mode"></a>启用虚空格模式  
  
1.  从“工具”菜单中选择“选项”。  
  
2.  展开“文本编辑器”文件夹，选择“所有语言”，全局设置此选项，或选择特定语言的文件夹。 （例如，若要仅在 Visual Basic 中打开行号，则在“文本编辑器”选项中选择“Basic”。）  
  
3.  选择“常规”选项，然后在“设置”下选择“启用虚空格”。  
  
    > [!NOTE]
    >  “虚空格”在“列选择”模式下启用。 如果未启用“虚空格”模式，插入点将从一行的末尾直接移动到下一行的第一个字符。  
  
## <a name="see-also"></a>另请参阅  
 [自定义编辑器](../ide/customizing-the-editor.md)   
 [在 Visual Studio 中自定义窗口布局](../ide/customizing-window-layouts-in-visual-studio.md)   
 [“选项”对话框 ->“环境”->“字体和颜色”](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
