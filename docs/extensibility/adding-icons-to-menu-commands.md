---
title: "将图标添加到菜单命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1cdf521228a1878fa94343418bd6a182f9707a2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-icons-to-menu-commands"></a>将图标添加到菜单命令
命令可以显示在菜单和工具栏上。 在工具栏上很常见的命令与只是一个图标 （以节省空间） 时在菜单上显示命令通常将出现并图标和文本。  
  
 图标是 16 像素宽 x 16 像素高和可以是 8 位颜色深度 （256 种颜色） 或 32 位颜色深度 （true 颜色）。 32 位颜色图标是首选。 通常在一个位图，单个水平行中排列图标，尽管允许多个位图。 此位图是以及可在位图中单个图标.vsct 文件中声明的。 请参阅参考的[位图元素](../extensibility/bitmaps-element.md)有关详细信息。  
  
## <a name="adding-an-icon-to-a-command"></a>将图标添加到命令  
 以下过程假定你的菜单命令与一个现有 VSPackage 项目。 若要了解如何执行此操作，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
1.  使用 32 位的颜色深度创建位图。 图标始终是 16 x 16，因此此位图必须是 16 像素高和 16 像素宽的倍数。  
  
     每个图标位于彼此相邻的单个行中的位图。 使用 alpha 通道指示位置的每个图标中的透明度。  
  
     如果你使用的 8 位颜色深度，使用洋红色，`RGB(255,0,255)`的透明度。 但是，32 位颜色图标是首选的。  
  
2.  将图标文件复制到 VSPackage 项目中的资源目录。 在解决方案资源管理器，将添加到项目的图标。 （选择资源，并在上下文菜单上单击添加，然后选择现有的项，然后选择你图标文件。）  
  
3.  在编辑器中打开.vsct 文件。  
  
4.  添加`GuidSymbol`具有的名称元素**testIcon**。 创建的 GUID (**工具 / 创建 GUID**，然后选择**注册表格式**并单击复制) 将其粘贴到`value`属性。 结果应如下所示：  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  添加`<IDSymbol>`图标。 `name`属性是图标的 ID 和`value`指示栏，其位置，如果有的话。 如果有一个图标，将添加 1。 结果应如下所示：  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  创建`<Bitmap>`中`<Bitmaps>`.vsct 文件来表示包含图标的位图的部分。  
  
    -   设置`guid`的名称值`<GuidSymbol>`你在上一步中创建的元素。  
  
    -   设置`href`为位图文件的相对路径的值 (在这种情况下**资源\\< 图标文件名\>**。  
  
    -   设置`usedList`IDSymbol 前面创建的值。 此属性指定要在 VSPackage 中使用的图标的以逗号分隔列表。 不在列表的图标是已排除的窗体编译。  
  
         位图块应如下所示：  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  在现有`<Button>`元素，设置`Icon`到前面创建的 GUIDSymbol 和 IDSymbol 值的元素。 下面是使用这些值的 Button 元素的示例：  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  测试您的图标。 生成项目并启动调试。 在实验实例中，找到命令。 它应显示图标添加。  
  
## <a name="see-also"></a>另请参阅  
 [扩展菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML 架构参考](../extensibility/vsct-xml-schema-reference.md)