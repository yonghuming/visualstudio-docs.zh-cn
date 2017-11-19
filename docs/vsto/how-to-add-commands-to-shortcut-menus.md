---
title: "如何： 向快捷菜单添加命令 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40b2bbb7c7b86665790a06feed288b0dd37272df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>如何：向快捷菜单添加命令
  本主题演示如何使用 VSTO 外接程序将命令添加到 Office 应用程序的快捷菜单中。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>将命令添加到 Office 的快捷菜单中  
  
1.  将“功能区 XML”  项添加到文档级项目或 VSTO 外接程序项目中。 有关详细信息，请参阅 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)。 内  
  
2.  在“解决方案资源管理器”中，选择“”  或“” 。  
  
3.  在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
     “ThisAddin”  类文件随即在代码编辑器中打开。  
  
4.  将下面的代码添加到 **ThisAddin** 类中。 此代码重写 CreateRibbonExtensibilityObject 方法，并返回到 Office 应用程序的功能区 XML 类。  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  在“解决方案资源管理器” 中，选择功能区 XML 文件。 默认情况下，功能区 XML 文件命名为 Ribbon1.xml。  
  
6.  在菜单栏上，依次选择 **“视图”**、 **“代码”**。  
  
     功能区 XML 文件随即在代码编辑器中打开。  
  
7.  在代码编辑器中添加 XML，该 XML 描述快捷菜单以及要添加到快捷菜单的控件。  
  
     下面的示例将向 Word 文档的快捷菜单添加按钮、菜单和库控件。 此快捷菜单的控件 ID 是 ContextMenuText。 有关 Office 2010 快捷控件的完整列表 ID，请参阅[Office 2010 帮助文件： Office Fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  在“解决方案资源管理器” 中，选择“MyRibbon.cs”  或“MyRibbon.vb” 。  
  
9. 向要处理的每个控件的 `Ribbon1` 类添加一个回叫方法。  
  
     下面的回叫方法将处理“我的按钮”  按钮。 此代码会在光标当前位置向活动文档添加一个字符串。  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>另请参阅  
 [Office UI 自定义项](../vsto/office-ui-customization.md)   
 [演练： 创建书签的快捷菜单](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [自定义 Office 2010 中的上下文菜单](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  