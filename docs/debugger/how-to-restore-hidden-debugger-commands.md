---
title: "如何： 还原隐藏的调试器命令 |Microsoft 文档"
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
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 561fa92e9797bd3a4343a4f2c6e23bd1e91ccab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-restore-hidden-debugger-commands"></a>如何：还原隐藏的调试器命令
安装 Visual Studio 时，系统会要求您为主要的编程语言选择一组默认的 IDE 设置。 某些语言的默认 IDE 设置可能会隐藏某些调试器命令。  
  
 如果要使用由默认 IDE 设置隐藏的调试器功能，可以使用以下过程将相应的命令重新添加到菜单中。  
  
### <a name="to-restore-hidden-debugger-commands"></a>还原隐藏的调试器命令  
  
1.  与打开，请在项目**工具**菜单上，单击**自定义**。  
  
2.  在**自定义**对话框中，单击**命令**选项卡。  
  
3.  在**菜单栏：**下拉列表中，选择**调试**你想要包含已还原的命令的菜单。  
  
4.  单击**添加命令...**按钮。  
  
5.  在**添加命令**框中，选择你想要添加，然后单击的命令**确定**。  
  
6.  重复上面的步骤以添加其他命令。  
  
7.  单击**关闭**完成后将命令添加到菜单。  
  
    > [!WARNING]
    >  某些菜单项仅在调试器处于特定模式（如运行模式或中断模式）下才显示。 因此，在完成这些步骤后，您所添加的项可能不会立即显示出来。  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>还原“自定义”对话框中不可用的命令  
 一些命令，尤其是那些分层菜单中不能从还原**自定义**对话框。 要还原这些命令，必须导入一组新的 IDE 设置。  
  
#### <a name="to-import-new-ide-settings"></a>导入新的 IDE 设置  
  
1.  上**工具**菜单上，单击**导入和导出设置**。  
  
2.  上**欢迎使用导入和导出设置向导**页上，单击**导入选定的环境设置**，然后单击**下一步**。  
  
3.  上**保存当前设置**页上，决定是否以保存你现有的设置，然后单击**下一步**。  
  
4.  上**选择要导入的设置集合**页上，在**默认设置**文件夹中，选择一个包含你想要使用的命令的开发设置集合。 如果不知道要选择哪个集合，请尝试**常规开发设置**或**Visual c + + 开发设置**，提供了大部分的调试器命令。  
  
5.  单击 **“下一步”**。  
  
6.  上**选择要导入设置**页上，在**选项**，请确保**调试**选择。 清除其他复选框，除非还要导入这些复选框对应的设置。  
  
7.  单击 **“完成”**。  
  
8.  上**导入完成**页上，查看任何与重置你的设置关联的错误**详细信息**。  
  
9. 单击 **“关闭”**。  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试器基础知识](../debugger/debugger-basics.md)