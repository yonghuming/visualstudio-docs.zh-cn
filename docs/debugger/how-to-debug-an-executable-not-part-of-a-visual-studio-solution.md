---
title: "如何：调试不属于 Visual Studio 解决方案的可执行文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试 [Visual Studio], 可执行文件"
  - "可执行文件, 在项目外调试"
  - "可执行文件, 导入"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：调试不属于 Visual Studio 解决方案的可执行文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有时可能需要调试不属于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目的可执行文件。  它可能是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外部创建的可执行文件，也可能是从其他用户处接收到的可执行文件。  
  
 解决此问题的常见方法是在 Visual Studio 外部启动可执行文件并使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器附加到该文件。  有关更多信息，请参见[附加到运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 附加到应用程序需要手动执行一些步骤，因此要花几秒钟的时间。  这一微小的延迟意味着如果尝试调试在启动过程中发生的问题，则这种附加将不会有帮助。  此外，如果调试的程序不等待用户输入而迅速完成，则可能没有时间附加到程序。  如果安装了 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]，则可以为此类程序创建 EXE 项目。  
  
### 为现有的可执行文件创建 EXE 项目  
  
1.  在**“文件”**菜单上，单击**“打开”**，然后选择**“项目”**。  
  
2.  在**“打开项目”**对话框中，单击**“文件名”**框旁边的下拉列表，然后选择**“所有项目文件”**。  
  
3.  找到可执行文件并单击**“确定”**。  
  
     这将创建一个包含该可执行文件的临时解决方案。  
  
### 将可执行文件导入到 Visual Studio 解决方案  
  
1.  在**“文件”**菜单中，指向**“添加项目”**，然后单击**“现有项目”**。  
  
2.  在**“添加现有项目”**对话框中，单击**“文件名”**框旁边的下拉列表，然后选择**“所有项目文件”**。  
  
3.  找到并选择可执行文件。  
  
4.  单击**“确定”**。  
  
5.  通过从**“调试”**菜单中选择执行命令（如**“启动”**）启动可执行文件。  
  
    > [!NOTE]
    >  并非所有编程语言都支持 EXE 项目。  如果需要使用此功能，请安装 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]。  
  
     调试没有源代码的可执行文件时，可用的调试功能将受到限制，无论是附加到正在运行的可执行文件还是将可执行文件添加到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案中。  如果可执行文件在生成时没有兼容格式的调试信息，则可用功能将进一步受到限制。  如果有源代码，则最佳方法是将源代码导入到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中并在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建可执行文件的调试版本。  
  
## 请参阅  
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [调试器安全](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/zh-cn/91e449e9-8b65-4123-960f-2107cd1f1cfd)