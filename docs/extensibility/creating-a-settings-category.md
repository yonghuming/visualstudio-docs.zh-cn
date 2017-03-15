---
title: "创建设置类别 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "创建类别配置文件设置"
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 39
---
# 创建设置类别
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本演练中创建 Visual Studio 设置类别，并使用它来保存到的值并从设置文件中还原值。 设置类别是一组显示为"自定义设置点;"的相关属性也就是说，作为中的复选框 **导入和导出设置** 向导。 \(您可以在找到 **工具** 菜单。\) 保存或还原为类别，设置和各项设置不会显示在该向导。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 通过派生其从创建类别设置 <xref:Microsoft.VisualStudio.Shell.DialogPage> 类。  
  
 若要开始本演练中，必须先完成的第一部分 [创建选项页](../extensibility/creating-an-options-page.md)。 生成的选项属性网格可以检查和更改类别中的属性。 在设置文件中保存的属性类别后，您将检查文件以查看如何存储的属性值。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建设置类别  
 在本部分中，使用自定义设置点来保存和还原设置类别的值。  
  
#### 若要创建设置类别  
  
1.  完成 [创建选项页](../extensibility/creating-an-options-page.md)。  
  
2.  打开 VSPackage.resx 文件并添加以下三个字符串资源︰  
  
    |名称|值|  
    |--------|-------|  
    |106|我类别|  
    |107|我的设置|  
    |108|OptionInteger 和 OptionFloat|  
  
     该名称的类别"My Category"、 对象"我的设置"，和类别描述"OptionInteger 和 OptionFloat"，这将创建资源。  
  
    > [!NOTE]
    >  这三个字段，只有类别名称都不显示在导入和导出设置向导。  
  
3.  在 MyToolsOptionsPackage.cs，添加 `float` 属性名为 `OptionFloat` 到 `OptionPageGrid` 类，如下面的示例所示。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid` 现在名为"My Category"类别包含两个属性， `OptionInteger` 和 `OptionFloat`。  
  
4.  添加 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 到 `MyToolsOptionsPackage` 类和为其提供 CategoryName"My Category"，为其指定的对象名"我的设置"，并将 isToolsOptionPage 设置为 true。 将 categoryResourceID、 objectNameResourceID 和 DescriptionResourceID 设置的 Id 前面创建的相应字符串资源。  
  
    ```c#  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  生成项目并启动调试。 在实验实例中应看到 **我的网格页** 现在具有整数和浮点值。  
  
## 检查设置文件  
 在此部分中，您将属性类别值导出到设置文件。 检查文件，然后将值导入回属性类别。  
  
1.  通过按 F5 在调试模式下启动项目。 这将启动实验实例。  
  
2.  打开 **工具 \/ 选项** 对话框。  
  
3.  在树视图中的左窗格中，展开 **My Category** ，然后单击 **我的网格页**。  
  
4.  值更改 **OptionFloat** 到 3.1416 和 **OptionInteger** 为 12。 单击“确定”。  
  
5.  在**“工具”**菜单上，单击**“导入和导出设置”**。  
  
     **导入和导出设置** 向导显示。  
  
6.  请确保 **导出选定的环境设置** 已选择，然后单击 **下一步**。  
  
     **选择要导出的设置** 页将出现。  
  
7.  单击 **我的设置**。  
  
     **说明** 变为 **OptionInteger 和 OptionFloat**。  
  
8.  请确保 **我的设置** 唯一类别，选择，然后单击是 **下一步**。  
  
     **名称您设置文件** 页将出现。  
  
9. 新的设置文件命名为 `MySettings.vssettings` 并将其保存在相应的目录中。 单击**“完成”**。  
  
     **导出完成** 页将报告已成功导出您的设置。  
  
10. 在 **文件** 菜单上，指向 **打开**, ，然后单击 **文件**。 找到 `MySettings.vssettings` 并将其打开。  
  
     您可以找到下一节 （你的 Guid 将不同） 的文件中导出的属性类别。  
  
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
  
     请注意通过添加一条下划线后跟对象名称的类别名称构成完整类别名称。 OptionFloat 和 OptionInteger 出现在类别，以及它们的导出值。  
  
11. 设置文件而不能更改其关闭。  
  
12. 在 **工具** 菜单上，单击 **选项**, ，展开 **My Category**, ，请单击 **我的网格页** 然后更改的值 **OptionFloat** 为 1.0 和 **OptionInteger** 为 1。 单击“确定”。  
  
13. 在 **工具** 菜单上，单击 **导入和导出设置**, ，选择 **导入选定的环境设置**, ，然后单击 **下一步**。  
  
     **保存当前设置** 页将出现。  
  
14. 选择 **否，仅导入新设置** ，然后单击 **下一步**。  
  
     **选择导入的设置集合** 页将出现。  
  
15. 选择 `MySettings.vssettings` 文件 **我的设置** 的树视图中的节点。 如果文件未出现在树视图中，请单击 **浏览** 和查找它。 单击**“下一步”**。  
  
     **选择设置应用于导入** 对话框随即出现。  
  
16. 请确保 **我的设置** 已选择，然后单击 **完成**。 当 **导入完成** 页出现时，请单击 **关闭**。  
  
17. 在 **工具** 菜单上，单击 **选项**, ，展开 **My Category**, ，请单击 **我的网格页** 并验证是否已恢复的属性类别值。