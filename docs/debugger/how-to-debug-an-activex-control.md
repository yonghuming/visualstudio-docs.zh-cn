---
title: "如何： 调试 ActiveX 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 932ccf7bdbea8fa68d0c2883d0ae8fd77eedf5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-activex-control"></a>如何：调试 ActiveX 控件
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在“工具”菜单上选择“导入和导出设置”。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
 若要调试 ActiveX 控件，必须指定一个容器（可执行文件）用于运行控件。  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>为调试会话指定容器  
  
1.  在“解决方案资源管理器”中，选择项目。  
  
2.  从**视图**菜单上，选择**属性页**。  
  
3.  在**项目属性页**对话框中，打开**配置属性**文件夹，并选择**调试**。  
  
4.  下**调试**类别中，找到**命令**属性。  
  
5.  指定容器的路径名。 例如，C:\Program Files\Internet Explorer\IEXPLORE.EXE。  
  
6.  如果指定 Internet Explorer 作为容器，且正在使用 Active Desktop，键入`/new`中**命令参数**框。  
  
7.  单击“确定”。  
  
     如果不指定某个容器中的**项目属性页**对话框中，你可以指定容器开始调试时。 当你选择执行命令来启动调试，[调试会话对话框中的可执行文件](../debugger/executable-for-debugging-session-dialog-box.md)显示。 在对话框中指定容器的路径名。  
  
## <a name="see-also"></a>另请参阅  
 [ActiveX 控件](/cpp/mfc/activex-controls)   
 [使用测试容器测试属性和事件](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [调试 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [调试器功能简介](../debugger/debugger-feature-tour.md)