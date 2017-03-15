---
title: "演练：动态自定义工具箱项配置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱 [Visual Studio SDK], 添加控件（自定义格式）"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# 演练：动态自定义工具箱项配置
本演练演示托管的 VSPackage 可以如何对 <xref:System.Drawing.Design.ToolboxItem> 对象的动态配置提供支持。  
  
> [!NOTE]
>  向工具箱添加自定义控件的最简单方法是使用 Visual Studio SDK 中包含的工具箱控件模板。 本主题与高级工具箱开发相关。  
>   
>  有关如何使用模板创建工具箱控件的详细信息，请参阅 [如何：创建使用 Windows 窗体的工具箱控件](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) 和 [创建 WPF 工具箱控件](../extensibility/creating-a-wpf-toolbox-control.md)。  
  
 本演练将指导你完成以下步骤：  
  
1.  通过使用 <xref:System.ComponentModel.ToolboxItemAttribute> 和 <xref:System.Drawing.ToolboxBitmapAttribute> 类，在 VSPackage 对象中添加并正确注册所有**工具箱**控件。  
  
2.  创建以下两个控件，并将其各自的图标添加到**工具箱**：  
  
    -   一个声明关联默认 <xref:System.Drawing.Design.ToolboxItem> 的控件。  
  
    -   一个控件，该控件声明派生自 <xref:System.Drawing.Design.ToolboxItem> 类的关联的自定义**工具箱**项。  
  
3.  编写 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 的实现，并通过执行以下操作对其进行注册：  
  
    1.  定义派生自 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 类的筛选器类，并指定此实现将作用于的 <xref:System.Drawing.Design.ToolboxItem> 实例。  
  
    2.  将引用筛选器类的 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> 应用到可实现 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Package> 类的类。  
  
4.  通过对可实现 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Package> 类的类应用 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>，将 VSPackage 注册为 <xref:System.Drawing.Design.ToolboxItem> 对象的提供程序。  
  
5.  在包加载时，使用反射来生成 VSPackage 提供的所有 <xref:System.Drawing.Design.ToolboxItem> 对象的列表。  
  
6.  创建 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件的处理程序。 执行此操作可保证正确加载 VSPackage 的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
7.  对 VSPackage 实现命令以强制重新初始化“工具箱”。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## Visual Studio 包项目模板的位置  
 可在“新建项目”对话框中的三个不同位置找到 Visual Studio 包项目模板：  
  
1.  在“Visual Basic 扩展性”之下。 项目的默认语言为 Visual Basic。  
  
2.  在“C\# 扩展性”之下。 项目的默认语言为 C\#。  
  
3.  在“其他项目类型扩展性”之下。 项目的默认语言为 C\+\+。  
  
## 创建托管的 VSPackage  
 完成以下过程以创建托管的 VSPackage。  
  
#### 创建托管的 VSPackage 以提供工具箱项  
  
1.  创建名为 `ItemConfiguration` 的 VSPackage。 有关详细信息，请参阅[演练：使用 Visual Studio 包模板创建菜单命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  在“Visual Studio 包”模板中，添加一个菜单命令。  
  
     对于 Visual Basic，将该命令命名为 `Initialize ItemConfigurationVB`；对于 Visual C\#，命名为 `Initialize ItemConfigurationCS`。  
  
3.  对于 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，向生成的项目中的导入的命名空间列表添加以下命名空间：  
  
    -   Company.ItemConfiguration  
  
    -   系统  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  添加对 <xref:System.Drawing.Design?displayProperty=fullName> .NET Framework 组件的引用。  
  
 如果使用多种语言按照本演练的步骤操作，则必须更新项目以消除所生成程序集的歧义。  
  
#### 消除 Visual Basic 和 Visual C\# Vspackage 的歧义  
  
1.  对于 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]：  
  
    1.  打开项目属性，并选择“应用程序”选项卡。  
  
         将程序集名称更改为 `ItemConfigurationVB`，并将默认命名空间更改为 `Company.ItemConfigurationVB`。  
  
    2.  选择“引用”选项卡。  
  
         更新导入的命名空间列表。  
  
         删除 Company.ItemConfiguration。  
  
         添加 Company.ItemConfigurationVB。  
  
2.  对于 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]：  
  
    1.  打开项目属性，并选择“应用程序”选项卡。  
  
         将程序集名称更改为 `ItemConfigurationCS`，并将默认命名空间更改为 `Company.ItemConfigurationCS`。  
  
    2.  在代码编辑器中打开 ItemConfigurationPackage 类。  
  
         若要使用重构工具对现有命名空间进行重命名，请右键单击现有命名空间名称 `ItemConfiguration`，指向“重构”，然后单击“重命名”。 将名称更改为 `ItemConfigurationCS`。  
  
3.  保存所有更改。  
  
#### 测试生成的代码  
  
1.  在 Visual Studio 的实验性配置单元中，编译并启动 VSPackage。  
  
2.  在“工具”菜单上，单击“初始化项配置 VB”或“初始化项配置 CS”。  
  
     执行此操作将打开一个包含文本的消息框，文本指示调用了包的菜单项句柄。  
  
3.  关闭 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 的实验版本。  
  
## 创建工具箱控件  
 在本部分中，你将创建并注册用户控件 `Control1`，该控件声明了关联的默认“工具箱”项。 你还将创建并注册另一个用户控件 `Control2` 及关联的自定义“工具箱”项 `Control2_ToolboxItem`，它派生自 <xref:System.Drawing.Design.ToolboxItem> 类。 有关如何创作 Windows 窗体控件和 <xref:System.Drawing.Design.ToolboxItem> 类的详细信息，请参阅 [设计时开发 Windows 窗体控件](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)。  
  
#### 创建默认和自定义工具箱项  
  
1.  使用 [演练：自动加载工具箱项](../Topic/Walkthrough:%20Autoloading%20Toolbox%20Items.md) 中的说明创建默认**工具箱**项和自定义**工具箱**项，如下所示。  
  
    1.  完成“创建将与默认 ToolboxItem 一起使用的**工具箱**控件。”过程。 更新 <xref:System.ComponentModel.DescriptionAttribute> 以引用此项目。  
  
         `Control1` 类的生成代码应类似于以下代码。  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  完成“创建可用于使用自定义 ToolboxItem 派生类的**工具箱**控件。”过程。 更新 <xref:System.ComponentModel.DescriptionAttribute> 以引用此项目。  
  
         `Control2` 和 `Control2_ToolboxItem` 类的生成代码应类似于以下代码。  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  保存文件。  
  
## 嵌入位图图标  
 应用于每个控件的 <xref:System.Drawing.ToolboxBitmapAttribute> 特性指定要与该控件关联的图标。 为这两个控件创建位图，并将它们命名如下：  
  
-   对于 `Control1` 类，命名为 `Control1.bmp`。  
  
-   对于 `Control2` 类，命名为 `Control2.bmp`。  
  
#### 为工具箱项嵌入位图图标  
  
1.  向项目添加新的位图，如下所示：  
  
    1.  在“解决方案资源管理器”中右击“VSPackage”项目，指向“添加”，然后单击“新建项”。  
  
    2.  在“添加新项”对话框中，选择“位图文件”，然后输入位图的名称。  
  
2.  使用位图编辑器创建一个 16x16 图标，如下所示。  
  
    1.  在**“视图”**菜单上，单击**“属性窗口”**。  
  
    2.  在“属性”窗口中，将“高度”和“宽度”设为 16。  
  
    3.  使用编辑器创建图标图像。  
  
3.  在“解决方案资源管理器”中右击该位图项，然后单击“属性”。  
  
4.  将“生成操作”属性设置为“嵌入的资源”。  
  
5.  保存所有打开的文件。  
  
## 添加动态工具箱配置提供程序  
 在本部分中，你将创建并注册一个实现 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 接口的类。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 实例化并使用此类以配置**工具箱**控件。  
  
> [!NOTE]
>  因为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境会实例化 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 的实现的实例，所以请勿对为 VSPackage 实现 <xref:Microsoft.VisualStudio.Shell.Package> 的类实现 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 接口。  
  
#### 创建并注册工具箱控件配置对象  
  
1.  在“解决方案资源管理器”中，向 ItemConfiguration 项目添加一个类，并将其命名为 `ToolboxConfig`。  
  
2.  将以下命名空间语句添加到文件。  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  确保 `ToolboxConfig` 类为 `public` 并实现 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 接口。  
  
4.  将 <xref:System.Runtime.InteropServices.GuidAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> 应用到 `ToolboxConfig` 类`.`  
  
    -   对于 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，使用程序集名称 `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"`。  
  
    -   对于 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]，使用程序集名称 `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"`。  
  
     此操作会将 `ToolboxConfig` 类限制为作用于由包含当前 VSPackage 的程序集提供的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     可通过单击“工具”菜单上的“创建 GUID”生成 GUID。 选择“带方括号的格式”，单击“复制”，然后将该 GUID 粘贴在代码中。 将关键字 `GUID` 更改为 `Guid`。  
  
5.  实现 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 接口的 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 方法，以使该方法仅作用于两个 <xref:System.Drawing.Design.ToolboxItem> 类：`Control1` 和 `Control2`。  
  
     <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 的实现将 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 的实例应用于这两个 <xref:System.Drawing.Design.ToolboxItem> 对象，使得：  
  
    -   由 `Control1` 实现的 <xref:System.Drawing.Design.ToolboxItem> 仅在可处理 <xref:System.Windows.Forms.UserControl> 对象的设计器的“工具箱”中可用。  
  
    -   由 `Control2` 实现的 <xref:System.Drawing.Design.ToolboxItem> 在处理 <xref:System.Windows.Forms.UserControl> 对象的设计器的“工具箱”中不可用。  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## 修改 VSPackage 实现  
 必须修改由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包模板提供的 VSPackage 的默认实现，才能执行以下操作：  
  
-   注册为**工具箱**项提供程序。  
  
-   注册为 VSPackage 提供动态**工具箱**控件配置的类。  
  
-   使用 <xref:System.Drawing.Design.ToolboxService> 加载 VSPackage 程序集提供的所有 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
-   处理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
#### 修改 VSPackage 上工具箱项提供程序的包实现  
  
1.  在代码编辑器中打开 ItemConfigurationPackage 类。  
  
2.  修改 `ItemConfigurationPackage` 类的声明，该类是解决方案中 <xref:Microsoft.VisualStudio.Shell.Package> 类的实现。  
  
    1.  将以下命名空间语句添加到文件。  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  若要将 VSPackage 注册为提供**工具箱**项，请向包应用 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>。 若要将 `ToolboxConfig` 类注册为提供**工具箱**控件动态配置，请向包应用 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>。  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 的唯一参数是由 VSPackage 提供的 <xref:System.Drawing.Design.ToolboxItem> 版本。 更改此值可强制 IDE 加载 VSPackage，即使它具有 <xref:System.Drawing.Design.ToolboxItem> 的较早缓存版本。  
  
    3.  在 `ItemConfiguration` 类中创建两个新的 `private` 字段，如下所示：  
  
         一个名为 `ToolboxItemList` 的 <xref:System.Collections.ArrayList> 成员，用于承载 `ItemConfiguration` 类所管理的 <xref:System.Drawing.Design.ToolboxItem> 对象的列表。  
  
         一个名为 `CategoryTab` 的 <xref:System.String>，它包含用于承载 `ItemConfiguration` 类所管理的 <xref:System.Drawing.Design.ToolboxItem> 对象的“工具箱”选项卡。  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     此修改得到的结果将类似于以下代码：  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  定义 `OnRefreshToolbox` 方法以处理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
     `OnRefreshToolbox` 方法使用 `ToolboxItemList` 字段中所包含的 <xref:System.Drawing.Design.ToolboxItem> 对象的列表，并执行以下操作：  
  
    -   从由 `CategoryTab` 字段定义的“工具箱”选项卡上删除所有 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
    -   向“工具箱”选项卡添加 `ToolboxItemList` 字段中列出的所有 <xref:System.Drawing.Design.ToolboxItem> 对象的新实例。  
  
    -   将“工具箱”选项卡设置为活动选项卡。  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  针对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]，在构造函数中，将 `OnRefreshToolbox` 方法注册为 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件的事件处理程序。  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  修改 `ItemConfigurationPackage` 中的 `Initialize` 方法，以便通过调用 <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName> 类的 <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> 方法填充 `ToolboxItemList` 字段。 “工具箱”服务将获取当前正在执行的程序集中定义的所有**工具箱**项类。**工具箱**事件处理程序使用 `ToolboxItemList` 字段加载**工具箱**项。  
  
     在 `Initialize` 方法的末尾添加以下代码。  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  作为练习，可以开发一种用于测试 VSPackage 或项的版本的机制，并且仅当 VSPackage 或 <xref:System.Drawing.Design.ToolboxItem> 的版本更改时才进行更新。  
  
## 初始化工具箱  
  
#### 实现命令以初始化工具箱  
  
-   在 `ItemConfigurationPackage` 类中，更改 `MenuItemCallBack` 方法，它是菜单项的命令处理程序。  
  
     通过使用以下代码，替换 `MenuItemCallBack` 方法的现有实现：  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## 生成并运行解决方案  
 通过使用在实验性配置单元中运行的 Visual Studio 的实例，可以运用本演练中的产品。  
  
#### 执行本演练  
  
1.  在 Visual Studio 的“生成”菜单上，单击“重新生成解决方案”。  
  
2.  按 F5 以在实验注册表配置单元中启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的第二个实例。  
  
     若要深入了解如何使用实验性配置单元，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
3.  单击“工具”菜单。  
  
     菜单顶部将显示名为“初始化 ItemConfiguration VB”或“初始化 ItemConfiguration CS”的命令，以及带有数字 1 的图标。  
  
4.  创建新的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Windows 窗体应用程序。  
  
     基于 <xref:System.Windows.Forms.Form> 的设计器随即出现。  
  
5.  将用户控件添加到项目中。  
  
     用户控件设计器随即出现。  
  
6.  固定打开的“工具箱”，并在两个设计视图之间进行切换。  
  
     请注意，哪个**工具箱**项可见，哪个隐藏，取决于焦点所在的设计器。  
  
7.  将第一个**工具箱**项拖动到用户控件上，以向该用户控件添加 `Control1` 的实例。  
  
8.  将第二个**工具箱**项拖动到窗体上，以向该窗体添加 `Control2` 的实例。  
  
9. 生成 Windows 应用程序。  
  
     “工具箱”中现提供用于应用程序的用户控件。  
  
10. 将应用程序的用户控件添加到窗体，然后重新生成并运行应用程序。  
  
     运行应用程序时，单击窗体上的每个控件可获取关联消息框。  
  
## 实现的分析  
 因为 `assemblyFilter` 参数存在于 <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> 类构造函数中，所以 `ToolboxConfg` 类的 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 方法仅作用于本演练中所生成的程序集的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
 因此，每当“工具箱”上的“ItemConfiguration 演练”类别处于活动状态时，即调用 `ToolboxConfg` 类的 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 方法，并且将 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 实例应用于由 `Control1` 和 `Control2` 实现的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
## 请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)   
 [注册工具箱支持功能](../misc/registering-toolbox-support-features.md)   
 [高级工具箱控件开发](/visual-cpp/misc/advanced-toolbox-control-development)   
 [工具箱演练](../misc/toolbox-walkthroughs.md)