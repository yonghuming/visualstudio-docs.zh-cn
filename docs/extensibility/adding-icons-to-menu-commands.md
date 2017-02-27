---
title: "将图标添加到菜单命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "将添加到工具栏的图标 [Visual Studio]"
  - "工具栏 [Visual Studio]，添加命令图标"
  - "命令 [Visual Studio]，添加图标"
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 将图标添加到菜单命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

命令可以显示在菜单和工具栏上。 在工具栏上很常见的命令与只是一个图标 （以节省空间） 时在菜单上显示命令通常显示带图标和文本。  
  
 图标是 16 像素宽乘 16 像素高，可以是 8 位颜色深度 （256 色） 或 32 位颜色深度 （真彩色）。 32 位颜色图标是首选。 通常在单个位图中单个水平行中排列图标，虽然允许多个位图。 此位图是在.vsct 文件以及可在位图中的单个图标中声明的。 请参阅参考的 [位图元素](../extensibility/bitmaps-element.md) 的更多详细信息。  
  
## 将图标添加到命令  
 以下过程假定您有一个现有的 VSPackage 项目，与菜单命令。 若要了解如何执行此操作，请参阅 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
1.  创建使用的颜色深度为 32 位的位图。 图标始终为 16 x 16 因此此位图必须为 16 像素高和宽为 16 像素倍数。  
  
     每个图标放置在单个行中彼此相邻的位图。 使用 alpha 通道来指示位置中的每个图标的透明度。  
  
     如果您使用 8 位颜色深度，使用洋红 `RGB(255,0,255)`, 的透明度。 但是，最好是 32 位颜色图标。  
  
2.  图标文件复制到 VSPackage 项目中的资源目录。 在解决方案资源管理器，将添加到项目的图标。 （选择资源，并在上下文菜单中单击添加然后现有项目，并选择图标文件。）  
  
3.  在编辑器中打开.vsct 文件。  
  
4.  添加 `GuidSymbol` 具有的名称元素 **testIcon**。 创建 GUID \(**工具 \/ 创建 GUID**, ，则可以选择 **注册表格式** 并单击复制\) 并将其粘贴到 `value` 属性。 结果应如下所示︰  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  添加 `<IDSymbol>` 图标。`name` 属性是图标的 ID 和 `value` 指示其在 strip 的位置。 如果只是一个图标，加 1。 结果应如下所示︰  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  创建 `<Bitmap>` 中 `<Bitmaps>` .vsct 文件来表示包含图标的位图的部分。  
  
    -   设置 `guid` 值的名称与 `<GuidSymbol>` 您在上一步中创建的元素。  
  
    -   设置 `href` 位图文件的相对路径的值 \(在这种情况下 **资源 \< 图标文件名称 \>**。  
  
    -   设置 `usedList` IDSymbol 先前创建的值。 此属性指定要在 VSPackage 中使用的图标的以逗号分隔列表。 已排除的窗体编译了不在列表的图标。  
  
         位图块应如下所示︰  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  在现有 `<Button>` 元素中，设置 `Icon` 先前创建的 GUIDSymbol 和 IDSymbol 值的元素。 下面是举例说明如何使用这些值的按钮元素︰  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  测试您的图标。 生成项目并启动调试。 在实验实例中，找到命令。 它应该显示图标添加。  
  
## 请参阅  
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML 架构参考](../extensibility/vsct-xml-schema-reference.md)