
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
ms.translationtype: HT
ms.sourcegitcommit: cc949cae43fe524771f43fe7e9261de3b4325649
ms.openlocfilehash: 8b8a7587687579e074d1b9ea1c9ae52a5f857fce
ms.contentlocale: zh-cn
ms.lasthandoff: 08/15/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>在 Visual Studio 中同步你的设置

使用同一个性化帐户在多台计算机上登录 Visual Studio 时，默认情况下你的设置会在所有计算机上进行同步。

## <a name="synchronized-settings"></a>同步设置

默认情况下，以下设置会进行同步。

- 开发设置（必须在首次运行 Visual Studio 时选择一组设置，但是可以随时更改选择。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。）

- “工具”|“选项”页中的以下选项：

    - “主题”和菜单栏大小写设置（位于“环境”、“常规”选项页上）

    - “环境”、“字体和颜色”选项页上的所有设置

    - 所有键盘快捷方式（位于“环境”、“键盘”选项页上）

    - “环境、选项卡和窗口”选项页上的所有设置

    - “环境”、“启动”选项页上的所有设置

    - “文本编辑器”选项页上的所有设置

    - “XAML 设计器”选项页上的所有设置

- 用户定义的命令别名。 有关如何定义命令别名的详细信息，请参阅 [Visual Studio 命令别名](../ide/reference/visual-studio-command-aliases.md)。

- “窗口”|“管理窗口布局”页中用户定义的窗口布局

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>关闭特定计算机上的同步设置

默认情况下启用 Visual Studio 的同步设置。 可以通过转到“工具”|“选项”|“环境”|“同步设置”页并取消选中复选框，来关闭计算机上的同步设置。  例如，如果决定不同步计算机 A 上的 Visual Studio 设置，那么计算机 A 上的任何设置更改将不会出现在计算机 B 或计算机 C 上。计算机 B 和 C 将继续彼此同步，但不与计算机 A 同步。

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>在 Visual Studio 系列产品和版本之间同步设置

可以在 Visual Studio 的任何版本（包括 Community 版本）之间同步设置。 Visual Studio 系列产品之间的设置也是同步的。 但是，这些系列产品中的每一个都可能具有它自己与 Visual Studio 不共享的设置。 例如，特定于计算机 A 上的某种产品的设置将与计算机 B 上的另一种产品共享，但不与计算机 A 或 B 上的 Visual Studio 共享。

## <a name="side-by-side-synchronized-settings"></a>并排同步设置

在 Visual Studio 15.3 及更高版本中，已停止在 Visual Studio 2017 的不同并排安装之间共享某些设置（如工具窗口布局），方法是将 `%userprofile%\Documents\Visual Studio 2017\Settings` 中的 `CurrentSettings.vssettings` 文件位置更改为类似于 `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings` 的特定于安装的文件夹。

注意：要使用新的特定于安装的设置，必须先完成全新安装。 将现有 Visual Studio 2017 安装升级到最新更新时，其会使用现有共享位置。 如果现在已拥有 Visual Studio 2017 的并行安装，并决定升级且希望使用特定于安装的新设置文件位置，请参阅以下步骤：

1. 升级之后，使用“导入\导出”设置向导将所有现有设置导出到 `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx` 文件夹之外的某个位置。
2. 打开适用于 VS 2017 的开发人员命令提示符（它属于已升级的 Visual Studio 安装），并在其中运行“devenv resetuserdata”。
3. 启动 Visual Studio，并从导出的设置文件中导入保存的设置。

## <a name="see-also"></a>请参阅

[个性化设置 IDE](../ide/personalizing-the-visual-studio-ide.md)

