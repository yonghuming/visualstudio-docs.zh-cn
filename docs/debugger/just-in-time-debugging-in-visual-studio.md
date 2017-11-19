---
title: "如何： 响应中实时调试器 |Microsoft 文档"
ms.custom: 
ms.date: 05/23/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: "48"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06beda1fdeda9f62d8f89b9458f488961d39fe29
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>如何： 响应中实时调试器

当你看到实时中时应采取的操作调试器对话框取决于你尝试执行的操作：

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>如果你想要修复或调试错误 （Visual Studio 用户）

- 你必须具有[安装 Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48146)若要查看有关错误的详细的信息，并尝试对其进行调试。 有关详细信息，请参阅[使用实时调试器调试](../debugger/debug-using-the-just-in-time-debugger.md)。 如果无法解决该错误并修复应用程序，联系应用程序的所有者以解决该错误。

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>如果你想要防止出现实时调试器对话框

你可以采取措施以防止实时中出现的调试器对话框。 如果应用程序处理错误，你可以正常运行应用程序。

1. （web 应用）如果你正在运行的 web 应用，你可以禁用脚本调试。

    对于 Internet Explorer 或 Edge，禁用脚本调试在 Internet 选项对话框中。 可以访问这些设置，从**控制面板** > **网络和 Internet** > **Internet 选项**(确切步骤取决于你版本的 Windows 和你的浏览器）。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    然后重新打开在其中找到错误的网页。 如果更改此设置不能解决此问题，联系以解决此问题的 web 应用程序所有者。

3. （visual Studio 用户）如果已安装的 Visual Studio （或如果你具有它之前安装和删除了它），[禁用中实时调试](../debugger/debug-using-the-just-in-time-debugger.md)，然后尝试再次运行该应用。

    > [!IMPORTANT]
    > 如果禁用中实时调试和应用程序遇到未经处理的异常 （错误），或者你就将相反，请参阅标准错误对话框中或应用程序将崩溃或挂起。 直到修复该错误 （由你或应用程序的所有者），应用程序将不会正常运行。

2. （ASP.NET 和 IIS）如果您要承载在 IIS 中的 ASP.NET Web 应用，禁用服务器端调试。

    在 IIS 管理器中，右键单击服务器节点并选择**切换到功能视图**。 在 ASP.NET 部分中，选择**.NET 编译**并确保你选择**False**为 （步骤会有所不同，在较旧版本的 IIS） 的调试行为。
  
## <a name="see-also"></a>另请参阅    
 [调试器基础知识](../debugger/debugger-basics.md)   
