---
title: "如何： 为调试指定.NET Framework 版本 |Microsoft 文档"
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace7dcdf236a551725dcc60e211ca98e3753e5cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>如何：指定用于调试的 .NET Framework 版本
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 调试器支持调试 Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的早期版本和当前版本。 如果从 Visual Studio 中启动应用程序，调试器始终可以标识的正确版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]正在调试的应用程序。 如果已在运行应用程序并使用**将附加到**，调试器可能始终无法识别的较旧版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 如果发生这种情况，您将收到一条错误消息，指出：  
  
 调试器对您的应用程序要使用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本进行了错误的假设。  
  
 在这些不常见的情况下，您可设置注册表项以指示调试器要使用的版本。  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>指定用于调试的 .NET Framework 版本  
  
1.  在 Windows\Microsoft.NET\Framework 目录中查找您计算机上安装的 .NET Framework 的版本。 这些版本号类似于：  
  
     `V1.1.4322`  
  
     识别正确的版本号并记录下来。  
  
2.  启动**注册表编辑器**(regedit)。  
  
3.  在**注册表编辑器**，打开 HKEY_LOCAL_MACHINE 文件夹。  
  
4.  导航到： HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     如果不存在该键，右击 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine，然后单击**新密钥**。 将新项`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`。  
  
5.  导航到 {449EC4CC-30D2-4032-9256-EE18EB41B62B} 之后, 查找**名称**列，并查找 CLRVersionForDebugging 项。  
  
    1.  如果键不存在，请右击 {449EC4CC-30D2-4032-9256-EE18EB41B62B}，然后单击**的新字符串值**。 然后右键单击新字符串值，单击**重命名**，和类型`CLRVersionForDebugging`。  
  
6.  双击**CLRVersionForDebugging**。  
  
7.  在**编辑字符串**框中，键入中的.NET Framework 版本号**值**框。 例如：V1.1.4322  
  
8.  单击“确定”。  
  
9. 关闭**注册表编辑器**。  
  
     如果开始调试时仍然收到错误消息，请验证是否已在注册表中正确输入了版本号。 还请验证您是否正在使用 Visual Studio 支持的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 调试器与 .NET Framework 当前版本及早期版本兼容，但可能与未来的版本不向前兼容。  
  
## <a name="see-also"></a>另请参阅  
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)