---
title: "如何： 设置调试和发布配置 |Microsoft 文档"
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4dc53ebb4a61d6d4740effa7b17b4d0a26d46a68
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>如何： 设置调试和发布 Visual Studio 中的配置
Visual Studio 项目具有针对你的程序的单独发布和调试配置。 顾名思义，生成调试版本的目的是用于调试，而生成发布版本的目的是用于最终发布分发。  
  
程序的调试配置使用完整符号调试信息编译，且不进行优化。 优化会使调试复杂化，因为源代码和生成的指令之间的关系更加复杂。  
  
程序的发布配置进行了完全优化，且不包含任何符号调试信息。 调试信息可以在.pdb 文件中生成[具体取决于编译器选项](#BKMK_symbols_release)使用。 创建.pdb 文件可能非常有用，如果以后还必须调试发行版本。  
  
有关生成配置的详细信息，请参阅[了解生成配置](../ide/understanding-build-configurations.md)。  
  
你可以更改生成配置从**生成**菜单上，从工具栏中，或在项目的属性页中。 项目属性页是特定于语言的。 下面的过程演示如何从菜单和工具栏更改生成配置。 有关如何更改中在不同语言中的项目的生成配置的详细信息，请参阅下面的另请参阅部分。  
  
## <a name="change-the-build-configuration"></a>更改生成配置  
  
1.  从**生成**菜单上，选择**Configuration Manager**，然后选择**调试**或**版本**。  
  
2.  在工具栏上，选择**调试**或**版本**从**解决方案配置**列表框。  
  
     ![工具栏生成配置](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Express 版中不提供此工具栏。 你可以使用**生成解决方案 F6**和**启动调试 F5**菜单项来选择配置。

## <a name="BKMK_symbols_release"></a>生成符号 (.pbd) 文件生成

对于大多数项目类型，.pdb 文件默认情况下，这两个调试生成和发布版本，但默认设置会有所不同，具体取决于你的特定项目类型和版本的 Visual Studio。 你可以配置是否编译器将生成.pdb 文件和哪种类型的调试信息包括。

> [!IMPORTANT] 
> 调试器只会为可执行文件加载与该可执行文件生成之时所创建的 .pdb 文件完全匹配的 .pdb 文件（即该 .pdb 文件必须是原始 .pdb 文件或其副本）。 有关详细信息，请参阅 [为什么 Visual Studio 要求调试器符号文件必须与同时生成的二进制文件完全匹配？](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

每个项目类型可能具有不同的方式设置这些选项。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>生成 C#、 ASP.NET、 或 Visual Basic 项目的符号文件

在 C# 中的调试配置的项目设置的详细信息，请参阅[项目 C# 调试配置的设置](../debugger/project-settings-for-csharp-debug-configurations.md)。 Visual Basic 中，请参阅[本主题](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)。

1. 右键单击解决方案资源管理器中的项目并选择**属性**。

2. 选择**版本**或**调试**中生成**配置**列表。

2. 选择**生成**设置，然后单击**高级**按钮。

    在 Visual Basic 中，你选择**编译**设置和**高级编译选项**按钮。

3. 选择**完整**，**可移植**，或**pdb_only**中**调试信息**列表框 (**生成调试信息**在 Visual Basic 中)。

    可移植的格式是为.NET 核心的最新的跨平台格式。 有关选项的详细信息，请参阅[高级生成设置对话框 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。

    ![在 C# 中生成的生成 Pdb](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. 生成你的项目。

    在可执行文件或主输出文件所在的文件夹中创建的符号文件。

### <a name="generate-symbol-files-for-a-c-project"></a>生成 c + + 项目的符号文件

1. 右键单击解决方案资源管理器中的项目并选择**属性**。

2. 选择**版本**或**调试**中生成**配置**列表。

2. 下**链接器 > 调试**，选择所需选项**生成调试信息**。

    在 c + + 调试配置的项目设置的详细信息，请参阅[项目 c + + 调试配置的设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)。

4. 配置生成程序数据库文件的选项

    在大多数 c + + 项目中，默认值是`$(OutDir)$(TargetName).pdb`，这将生成.pdb 文件的输出文件夹中。

    ![在 c + + 生成的生成 Pdb](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. 生成你的项目。

    在可执行文件或主输出文件所在的文件夹中创建的符号文件。
  
## <a name="see-also"></a>另请参阅  
 [在 Visua Studio 调试器中指定符号 (.pdb) 文件和源文件](../debugger/debugger-settings-and-preparation.md)  
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [C + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [对于 C# 的项目设置调试配置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [调试配置适用于 Visual Basic 项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [如何：创建和编辑配置](../ide/how-to-create-and-edit-configurations.md)   
 [调试和发布项目配置](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)