---
title: "调试准备： Visual c + + 项目类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c5698fef83134e9cdd7451a1ec43ace33dbb463
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-preparation-visual-c-project-types"></a>调试准备：Visual C++ 项目类型
本节描述如何调试用 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 项目模板创建的基本项目类型。  
  
 请注意，创建 Dll 作为其输出这些项目类型已被分组到[调试 DLL 项目](../debugger/debugging-dll-projects.md)由于它们共享的常见功能。  
  
##  <a name="BKMK_In_this_topic"></a> 主题内容  
 [建议的属性设置](#BKMK_Recommended_Property_Settings)  
  
 [Win32 项目](#BKMK_Win32_Projects)  
  
-   [调试 C 或 c + + Win32 应用程序](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [若要手动设置调试配置](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Windows 窗体应用程序 (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a>建议的属性设置  
 应以相同的方式设置所有非托管调试方案的某些属性。 以下各表显示了建议的属性设置。 未在此处列出的设置可能有各种不同的非托管项目类型。 有关详细信息，请参阅[用于 c + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>配置属性 &#124;C/c + + &#124;优化节点  
  
|属性名|设置|  
|-------------------|-------------|  
|**优化**|设置为**已禁用 (/ 0 d)。** 优化代码更难调试，因为生成的指令与源代码并不直接对应。 如果发现程序具有只在优化代码中出现的 bug，则可以打开此设置，但应记住中显示的代码**反汇编**窗口从可能与你在源代码中看到的内容不匹配的优化源生成windows。 其他功能（如单步执行）可能不会像预期的那样执行。|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>配置属性 &#124;链接器 &#124;调试节点  
  
|属性名|设置|  
|-------------------|-------------|  
|**生成调试信息**|你应始终将此选项设置为**是 (/debug)**创建调试符号和所需的调试文件。 在应用程序进入成品阶段时，可以将其设置为关闭。|  
  
 [主题内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a>Win32 项目  
 Win32 应用程序是用 C 或 C++ 编写的传统 Windows 程序。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中调试此类应用程序非常简单。  
  
 Win32 应用程序包括 MFC 应用程序和 ATL 项目。 Win32 应用程序使用 Windows API，也可使用 MFC 或 ATL，但不使用公共语言运行时 (CLR)。 但是，它们可以调用使用 CLR 的托管代码。  
  
 下面的过程解释如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中调试 Win32 项目。 调试 Win32 应用程序的另一种方法是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之外启动并附加到该应用程序。 有关详细信息，请参阅[附加到运行进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a>调试 C 或 c + + Win32 应用程序  
  
1.  在 Visual Studio 中打开项目。  
  
2.  上**调试**菜单上，选择**启动**。  
  
3.  调试使用中讨论的技术[调试器基础知识](../debugger/debugger-basics.md)。  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a>若要手动设置调试配置  
  
1.  上**视图**菜单上，单击**属性页**。  
  
2.  单击**配置属性**节点，以打开它，如果它尚不  
  
3.  选择**常规**，并将的值设置**输出**行到**调试**。  
  
4.  打开**C/c + +**节点，然后选择**常规**。  
  
     在**调试**行指定的调试信息要由编译器生成的类型。 可以选择的值包括**程序数据库 (/Zi)**或**用于 ' 编辑并继续 (/ZI) 的程序数据库**。  
  
5.  选择**优化**，然后在**优化**行中，选中**已禁用 (/ 0d)**从下拉列表。  
  
     优化代码更难调试，因为生成的指令与源代码并不直接对应。 如果发现程序具有只出现在优化代码中的 bug，则可以打开此设置，但应记住“反汇编”窗口中显示的代码是从可能与在源窗口中见到的内容不匹配的优化源生成的。 有些功能（如单步执行）显示的断点和执行点有可能不正确。  
  
6.  打开**链接器**节点，然后选择**调试**。 在第一个**生成**行中，选中**是 (/debug)**从下拉列表。 调试期间应始终这样设置。  
  
 有关详细信息，请参阅[用于 c + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
 [主题内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a>Windows 窗体应用程序 (.NET)  
 **Windows 窗体应用程序 (.NET)**模板创建[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]Windows 窗体应用程序。 有关详细信息，请参阅 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中调试此类应用程序类似于在托管的 Windows 窗体应用程序中进行调试。  
  
 用项目模板创建 Windows 窗体项目时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将自动为调试和发布配置创建所需的设置。 如果有必要，你可以在更改这些设置**\<项目名称 > 属性页**对话框。 有关详细信息，请参阅[调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
 有关详细信息，请参阅[用于 c + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
 调试 Windows 窗体应用程序的另一种方法是从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外部启动应用程序并附加到它上面。 有关详细信息，请参阅[将附加到正在运行的程序或多个程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 [主题内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>另请参阅  
 [Debugger Basics](../debugger/debugger-basics.md) （调试器基础知识）  
 [C + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [将附加到正在运行的程序或多个程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)   
 [如何： 创建 Windows 应用程序项目](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)