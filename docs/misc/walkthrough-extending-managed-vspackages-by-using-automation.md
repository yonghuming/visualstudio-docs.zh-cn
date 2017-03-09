---
title: "演练：通过使用自动化来扩展托管 VSPackage | Microsoft Docs"
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
  - "托管 VSPackage, 使用自动化扩展"
  - "自动化 [Visual Studio SDK], 演练"
  - "自动化 [Visual Studio SDK], 托管 VSPackage"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# 演练：通过使用自动化来扩展托管 VSPackage
此演练演示如何使用自动化来创建操作 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 的托管 VSPackage。 创建一个托管 VSPackage 示例，然后在生成的 VSPackage 中使用自动化方法，以在“输出”窗口中显示 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 属性。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关更多信息，请参见[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## Visual Studio 包项目模板的位置  
 可在“新建项目”对话框中的三个不同位置找到 Visual Studio 包项目模板：  
  
1.  在“Visual Basic 扩展性”之下。 项目的默认语言为 Visual Basic。  
  
2.  在“C\# 扩展性”之下。 项目的默认语言为 C\#。  
  
3.  在“其他项目类型扩展性”之下。 项目的默认语言为 C\+\+。  
  
### 创建托管 VSPackage  
  
1.  创建名为 `Auto` 的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包项目。  
  
     有关如何创建托管 VSPackage 的详细信息，请参阅[演练：使用 Visual Studio 包模板创建菜单命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  在“选择编程语言”页上，将语言设置为 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]。  
  
3.  在“基本 VSPackage 信息”页中，保留默认值。  
  
4.  在“选择 VSPackage 选项”页上，选中“菜单命令”复选框。  
  
5.  在“命令选项”页上，将“命令名称”更改为 `Auto`。  
  
6.  点击“完成”按钮。  
  
     该模板会生成一个名为 Auto 的托管项目。  
  
7.  生成解决方案并确认编译时不会产生错误。  
  
### 调用自动化模型  
  
1.  在“解决方案资源管理器”中，右键单击 Auto 项目节点，然后依次单击“添加”和“引用”。  
  
2.  在“引用”对话框的“.NET”选项卡上，双击“EnvDTE”。  
  
     此操作将添加对 EnvDTE 自动化命名空间的引用。  
  
3.  在 AutoPackage 文件中，添加以下命名空间引用。  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  在 AutoPackage 文件中，将 `MenuItemCallback` 方法的主体替换为下面的行：  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 此代码将调用 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 以获取表示 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 的 <xref:EnvDTE.DTE> 自动化项目。`MenuItemCallback` 中的自动化代码在“输出”窗口创建了一个名为“测试”的新窗格。 然后在新的“输出”窗格中写入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 名称和版本。  
  
1.  生成 Auto 项目并按 F5 在调试模式下启动该项目。  
  
     这将启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 实验性生成 \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\)。  
  
    > [!NOTE]
    >  目前，将打开两个版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
2.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp 中，在“工具”菜单上，单击“Auto”。  
  
     此操作将在“输出”窗口中打开一个名为“测试”的新窗格，该窗格中将显示以下内容：  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     其中，x.xx 是最新的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本号。  
  
     有关自动化示例的详细信息，请参阅[适用于 Visual Studio 的自动化示例](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en)。  
  
## 请参阅  
 [扩展 Visual Studio 环境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)