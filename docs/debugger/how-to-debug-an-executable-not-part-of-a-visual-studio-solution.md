---
title: "如何： 调试不属于 Visual Studio 解决方案的可执行文件 |Microsoft 文档"
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
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be07be0e1374360a96b6672b095dcc039c6bb4f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>如何： 调试不属于 Visual Studio 解决方案的可执行文件
有时，你可能想要调试的可执行文件 （.exe 文件） 不属于[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。 它可能是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外部创建的可执行文件，也可能是从其他用户处接收到的可执行文件。  
  
解决此问题的常见方法是在 Visual Studio 外部启动可执行文件并使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器附加到该文件。 有关详细信息，请参阅[附加到运行进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
附加到应用程序需要手动执行一些步骤，因此要花几秒钟的时间。 这一微小的延迟意味着如果尝试调试在启动过程中发生的问题，则这种附加将不会有帮助。 此外，如果调试的程序不等待用户输入而迅速完成，则可能没有时间附加到程序。 如果你有[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]和[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]安装，你可以创建这样的程序的 EXE 项目。

> [!NOTE]
>  并非所有编程语言都支持 EXE 项目。

调试不属于 Visual Studio 解决方案的可执行文件时，无论是附加到正在运行的可执行文件还是添加到可执行文件，可用的调试功能可能会受到限制，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]解决方案。

- 如果有源代码，则最佳方法是将源代码导入到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中并在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建可执行文件的调试版本。
- 如果你没有源代码，并生成可执行文件时没有[的调试信息](../debugger/how-to-set-debug-and-release-configurations.md)兼容的格式，在可用的调试功能是非常有限。 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>为现有的可执行文件创建 EXE 项目  
  
1.  上**文件**菜单上，单击**打开**和选择**项目**。  
  
2.  在**打开项目**对话框中，单击旁边的下拉列表**文件名**框中，然后选择**所有项目文件**。  
  
3.  找到可执行文件，并单击**确定**。  

    这将创建一个包含该可执行文件的临时解决方案。

5.  通过选择执行命令，如启动可执行文件**启动**，从**调试**菜单。    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>将可执行文件导入到 Visual Studio 解决方案  
  
1.  上**文件**菜单上，指向**添加项目**，然后单击**现有项目**。  
  
2.  在**添加现有项目**对话框中，单击旁边的下拉列表**文件名**框中，然后选择**所有项目文件**。  
  
3.  找到并选择可执行文件。  
  
4.  单击“确定”。  
  
5.  通过选择执行命令，如启动可执行文件**启动**，从**调试**菜单。    
  
## <a name="see-also"></a>另请参阅  
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [调试器安全](../debugger/debugger-security.md)   
 [DBG 文件](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)