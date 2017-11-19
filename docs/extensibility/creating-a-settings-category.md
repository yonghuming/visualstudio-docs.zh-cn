---
title: "创建设置类别 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: "39"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016aac6f0e23b626b9023b978efa27e76924c6c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-settings-category"></a>创建设置类别
在本演练中，通过创建 Visual Studio 设置类别，并通过使用它来保存到的值，并从设置文件还原值。 设置类别是一组显示为"自定义设置点;"的相关属性的也就是说，作为处于的复选框**导入和导出设置**向导。 (你可找到该**工具**菜单。)保存或还原为类别，设置和单个设置不会显示在该向导。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
 通过派生从创建设置类别<xref:Microsoft.VisualStudio.Shell.DialogPage>类。  
  
 若要在开始本演练，必须先完成的第一部分[创建选项页](../extensibility/creating-an-options-page.md)。 生成的选项属性网格，可以检查和更改类别中的属性。 在设置文件中保存属性类别后，你将检查文件以查看如何存储的属性值。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-settings-category"></a>创建设置类别  
 在本部分中，你可以使用自定义设置点用于保存和还原设置类别的值。  
  
#### <a name="to-create-a-settings-category"></a>若要创建设置类别  
  
1.  完成[创建选项页](../extensibility/creating-an-options-page.md)。  
  
2.  打开 VSPackage.resx 文件并添加以下三个字符串资源：  
  
    |名称|值|  
    |----------|-----------|  
    |106|我类别|  
    |107|我的设置|  
    |108|OptionInteger 和 OptionFloat|  
  
     该名称的类别"我的类别"、 对象"我的设置"，和类别描述"OptionInteger 和 OptionFloat"，这将会创建资源。  
  
    > [!NOTE]
    >  这三种导入和导出设置向导中未显示仅类别名称。  
  
3.  在 MyToolsOptionsPackage.cs，添加`float`属性名为`OptionFloat`到`OptionPageGrid`类，如下面的示例中所示。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid`类别现在名为"我的类别"包含两个属性时，`OptionInteger`和`OptionFloat`。  
  
4.  添加<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>到`MyToolsOptionsPackage`类并为其提供 CategoryName"我的类别"，请为其提供 ObjectName"我的设置"，并将 isToolsOptionPage 设置为 true。 设置为 Id 前面创建的相应字符串资源的 categoryResourceID、 objectNameResourceID 和 DescriptionResourceID。  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  生成项目并启动调试。 在实验实例中您应该会看到**我网格页**现在具有整数和浮点值。  
  
## <a name="examining-the-settings-file"></a>检查设置文件  
 在此部分中，你将属性类别值导出到设置文件。 检查文件，然后将值导入回属性类别。  
  
1.  通过按 F5 在调试模式下启动项目。 这将启动实验实例。  
  
2.  打开**工具 / 选项**对话框。  
  
3.  在左窗格中的树视图中，展开**我类别**，然后单击**我网格页**。  
  
4.  更改的值**OptionFloat**到 3.1416 和**OptionInteger**和 12 之间。 单击“确定”。  
  
5.  上**工具**菜单上，单击**导入和导出设置**。  
  
     **导入和导出设置**向导显示。  
  
6.  请确保**导出选定的环境设置**已选择，然后单击**下一步**。  
  
     **选择要导出的设置**页将出现。  
  
7.  单击**我的设置**。  
  
     **说明**更改为**OptionInteger 和 OptionFloat**。  
  
8.  请确保**我的设置**是唯一的类别，选择，然后单击**下一步**。  
  
     **名称你设置文件**页将出现。  
  
9. 将新的设置文件命名`MySettings.vssettings`并将其保存在相应的目录中。 单击 **“完成”**。  
  
     **导出完成**页将报告已成功导出你的设置。  
  
10. 上**文件**菜单上，指向**打开**，然后单击**文件**。 找到`MySettings.vssettings`并将其打开。  
  
     你可以查找 （你的 Guid 将不同） 的文件的以下部分中导出的属性类别。  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     请注意，通过添加到类别名称后, 跟对象名称以下划线形成完整的类别名称。 OptionFloat 和 OptionInteger 显示在类别，以及其导出的值。  
  
11. 关闭而不能更改的设置文件。  
  
12. 上**工具**菜单上，单击**选项**，展开**我类别**，单击**我网格页**然后将更改的值**OptionFloat**为 1.0 和**OptionInteger**为 1。 单击“确定”。  
  
13. 上**工具**菜单上，单击**导入和导出设置**，选择**导入选定的环境设置**，然后单击**下一步**。  
  
     **保存当前设置**页将出现。  
  
14. 选择**否，仅导入新设置**，然后单击**下一步**。  
  
     **选择设置集合导入**页将出现。  
  
15. 选择`MySettings.vssettings`文件中**我的设置**树视图的节点。 如果文件不未出现在树视图中，单击**浏览**并且找到它。 单击 **“下一步”**。  
  
     **选择导入的设置**对话框随即出现。  
  
16. 请确保**我的设置**已选择，然后单击**完成**。 当**导入完成**页出现时，单击**关闭**。  
  
17. 上**工具**菜单上，单击**选项**，展开**我类别**，单击**我网格页**并验证属性类别值具有已还原。