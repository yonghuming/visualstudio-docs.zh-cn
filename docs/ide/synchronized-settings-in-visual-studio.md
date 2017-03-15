---
title: "在 Visual Studio 中同步你的设置 | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 4166ed8bfa0234e1cc453bd045974b412f87ae42
ms.openlocfilehash: a1a310aa6bf0e3d0042f35f5c49612f33b89fb61
ms.lasthandoff: 02/22/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>在 Visual Studio 中同步你的设置
使用同一个性化帐户在多台计算机上登录 Visual Studio 时，默认情况下你的设置会在所有计算机上进行同步。

## <a name="synchronized-settings"></a>同步设置  
 默认情况下，以下设置会进行同步。  

-   开发设置（必须在首次运行 Visual Studio 时选择一组设置，但是可以随时更改选择。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  

-   “工具”|“选项”页中的以下选项：  

    -   “主题”和菜单栏大小写设置（位于“环境”、“常规”选项页上）  

    -   “环境”、“字体和颜色”选项页上的所有设置  

    -   所有键盘快捷方式（位于“环境”、“键盘”选项页上）  

    -   “环境、选项卡和窗口”选项页上的所有设置  

    -   “环境”、“启动”选项页上的所有设置  

    -   “文本编辑器”选项页上的所有设置  

-   “XAML 设计器”选项页上的所有设置  

-   用户定义的命令别名。 有关如何定义命令别名的详细信息，请参阅 [Visual Studio 命令别名](../ide/reference/visual-studio-command-aliases.md)。  

-   “窗口”|“管理窗口布局”页中用户定义的窗口布局  

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>关闭特定计算机上的同步设置  
 默认情况下启用 Visual Studio 的同步设置。 可以通过转到“工具”|“选项”|“环境”|“同步设置”页并取消选中复选框，来关闭计算机上的同步设置。  例如，如果你决定不同步计算机 A 上的 Visual Studio 设置，那么计算机 A 上的任何设置更改将不会出现在计算机 B 或计算机 C 上。计算机 B 和 C 将继续彼此同步，但不与计算机 A 同步。  

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>在 Visual Studio 系列产品和版本之间同步设置  
 可以在 Visual Studio 的任何版本（包括 Community 版本）之间同步设置。 Visual Studio 系列产品之间的设置也是同步的。 但是，这些系列产品中的每一个都可能具有它自己与 Visual Studio 不共享的设置。 例如，特定于计算机 A 上的某种产品的设置将与计算机 B 上的另一种产品共享，但不与计算机 A 或 B 上的 Visual Studio 共享。  

## <a name="see-also"></a>另请参阅  
 [个性化设置 IDE](../ide/personalizing-the-visual-studio-ide.md)

