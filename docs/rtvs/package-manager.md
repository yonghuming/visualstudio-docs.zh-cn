---
title: "针对 Visual Studio 的 R 工具中的程序包管理器 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>程序包管理器

针对 Visual Studio 的 R 工具 (RTVS) 程序包管理器是一个用于管理 R 程序包的UI。 若要打开它，请选择“R 工具”>“窗口”>“程序包”或按 Ctrl+7。

如下所述，程序包管理器包含三个选项卡。 所有选项卡均在左侧显示相关程序包的列表，右侧显示所选程序包的特定详细信息，包括程序包版本、说明、许可证、安装位置和其他相关信息的链接。 右上角的搜索框可用于筛选列表。

> [!Tip]
> 在选项卡之间切换时，搜索框中的词语保持有效。

- “可用”用于浏览要安装的程序包。 如果已安装程序包，右侧的“安装”按钮将改为“卸载”。

    ![针对 Visual Studio 的 R 工具程序包管理器中的可用程序包选项卡](~/rtvs/media/package-manager-available.png)

- “已安装”显示所有已安装和已加载的程序包。 程序包旁边的绿色园点指示该程序包已加载到 R 会话中。 左侧的红色 X 图标或右侧的“卸载”按钮可用于卸载程序包。 如果有较新版本可用，可通过已安装程序包右侧的蓝色向上箭头更新程序包。

    ![针对 Visual Studio 的 R 工具程序包管理器中的已安装程序包选项卡](~/rtvs/media/package-manager-installed.png)

- “已加载”仅显示已加载到 R 会话中的程序包，因此显示的所有程序包都会带有绿色园点。 还可在此处卸载和更新程序包。

    ![针对 Visual Studio 的 R 工具程序包管理器中的已加载程序包选项卡](~/rtvs/media/package-manager-loaded.png)

## <a name="package-locations"></a>程序包位置

程序包安装在以下位置:

- RTVS 随附的核心程序包安装在 `C:\Program Files\Microsoft\R Client\R_SERVER\library` 中
- 其他程序包的安装位置为：`%userprofile%\Documents\R\win-library\3.3`

