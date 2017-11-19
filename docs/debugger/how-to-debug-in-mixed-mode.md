---
title: "如何： 在混合模式下调试 |Microsoft 文档"
ms.custom: 
ms.date: 06/19/2017
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
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e319f0e6c9ca6197930858407a2177e9fe246907
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-in-mixed-mode"></a>How to: Debug in Mixed Mode
以下过程描述如何调试托管代码和本机代码，这一过程也称作混合模式调试。 根据 DLL 或应用程序是否用本机代码编写，有两种方案可以用来进行调试：  
  
-   调用 DLL 的调用应用程序是用本机代码编写的。 在这种情况下 DLL 是托管的，托管调试器和本机调试器都必须启用，以调试托管代码和本机代码。 你可以在选中此**\<项目 > 属性页**对话框。 具体如何检查取决于是从 DLL 项目中启动调试，还是从调用应用程序项目中启动调试。  
  
-   调用 DLL 的调用应用程序是用托管代码编写的，而 DLL 是用本机代码编写的。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。

如果你没有调用应用程序到项目访问权限，您可以调试 DLL 项目中的 DLL。 有关详细信息，请参阅 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)。 你不需要使用混合调试仅 DLL 项目。
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>若要启用混合模式调试 （c + + 调用应用程序）  
  
1.  在**解决方案资源管理器**，选择本机项目。
  
2.  上**视图**菜单上，单击**属性页**。
  
3.  在**\<项目 > 属性页**对话框框中，展开**配置属性**节点，，然后选择**调试**。  
  
4.  设置**调试器类型**到**混合**或**自动**。

    ![启用混合的模式调试](../debugger/media/dbg-mixed-mode-from-native.png "启用混合的模式调试")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>若要启用混合模式调试 (C# 或 VB 调用应用程序）  
  
1.  在**解决方案资源管理器**，选择托管的项目。  
  
2.  上**视图**菜单上，单击**属性页**。  
  
3.  在**\<项目 > 属性页**对话框中，选择**调试**选项卡上，然后选择**启用本机代码调试**

    ![启用本机代码调试](../debugger/media/dbg-mixed-mode-from-csharp.png "启用本机代码调试")
  
## <a name="see-also"></a>另请参阅  
 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)