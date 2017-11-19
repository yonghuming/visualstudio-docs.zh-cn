---
title: "新的项目生成： 实质上，第一部分 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efe08d9e23f1a77fd68df2bdba4389e7b7955b11
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="new-project-generation-under-the-hood-part-one"></a>新的项目生成： 实质上，第一部分
有没有想过有关如何创建你自己的项目类型？ 想要知道什么实际发生时创建新项目？ 让我们了解一下实质上的，请参阅什么现状。  
  
 有多个 Visual Studio 协调为你的任务：  
  
-   其中显示所有可用的项目类型的树。  
  
-   它显示的每个项目类型的应用程序模板列表，并可让你选择一个。  
  
-   它收集应用程序，例如项目名称和路径的项目信息。  
  
-   它将此信息传递到的项目工厂。  
  
-   它生成当前解决方案中的项目项和文件夹。  
  
## <a name="the-new-project-dialog-box"></a>新项目对话框  
 所有它将开始时选择新项目的项目类型。 通过单击一下**新项目**上**文件**菜单。 **新项目**显示对话框，请查找如下所示：  
  
 ![新建项目对话框](../../extensibility/internals/media/newproject.gif "新建项目")  
  
 让我们仔细看。 **项目类型**树列出了你可以创建的各种项目类型。 当你选择项目类型，如**Visual C# Windows**，你将看到应用程序模板，以帮助你入门的列表。 **Visual Studio 已安装的模板**由 Visual Studio 安装，并可供你计算机的任何用户。 创建或收集的新模板可以添加到**我的模板**和仅对你可用。  
  
 当选择模板与相似**Windows 应用程序**，应用程序类型的描述将显示在对话框中; 在本例中，**用于使用 Windows 用户界面创建应用程序的项目**。  
  
 在底部**新项目**对话框中，你将看到收集的详细信息的几个控件。 你看到的控件取决于项目类型，但它们通常包括一个项目**名称**文本框中，**位置**文本框和相关**浏览**按钮，然后**解决方案名称**文本框和相关**创建解决方案的目录**复选框。  
  
## <a name="populating-the-new-project-dialog-box"></a>填充新的项目对话框  
 其中未**新项目**对话框中获取其信息从？ 在工作在这里，不建议使用其中一个有两种机制。 **新项目**对话框中将合并，并显示从这两种机制获取的信息。  
  
 较旧的 （已弃用） 方法采用.vsdir 文件和系统注册表项。 Visual Studio 打开时，将运行此机制。 较新的方法使用.vstemplate 文件。 此机制运行 Visual Studio 初始化时，例如，通过运行  
  
```  
devenv /setup  
```  
  
 或  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>项目类型  
 位置和名称**项目类型**根节点，如**Visual C#**和**其他语言**，由系统注册表项。 组织的子节点，如**数据库**和**智能设备**，镜像包含相应的.vstemplate 文件的文件夹的层次结构。 让我们看一下根节点第一次。  
  
#### <a name="project-type-root-nodes"></a>项目类型的根节点  
 当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是初始化，遍历系统注册表项 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs 来生成，并将命名的根节点的子项**项目类型**树。 此信息缓存供以后使用。 看一看 TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 键。 每个条目为 VSPackage 的 GUID。 子项的名称 （/ 1） 将被忽略，但它的存在指示这是**项目类型**根节点。 根节点可能有多个控制在其外观的子项**项目类型**树。 让我们看一下其中一些。  
  
##### <a name="default"></a>(默认)  
 这是根节点名称的本地化字符串的资源 ID。 字符串资源位于附属 DLL 选择的 VSPackage GUID。  
  
 在示例中，VSPackage GUID 是  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 和资源 ID （默认值） 的根节点 （/ 1） 是 # 2345年  
  
 如果你查找附近的包密钥中的 GUID，并且检查 SatelliteDll 子项，您可以找到包含字符串资源的程序集的路径：  
  
 \<Visual Studio 安装路径 > \VC#\VCSPackages\1033\csprojui.dll  
  
 若要验证这一点，打开文件资源管理器，并将 csprojui.dll 拖到 Visual Studio 目录... 字符串表显示资源 # 2345年具有标题**Visual C#**。  
  
##### <a name="sortpriority"></a>SortPriority  
 这将确定的位置中的根节点**项目类型**树。  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 优先级，越低数越高在树中的位置。  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 此子项是否存在，然后由开发人员设置对话框中控制根节点的位置。 例如，  
  
 DeveloperActivity REG_SZ VC #  
  
 指示 Visual C# 将会根节点是否 Visual Studio 设置为[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]开发。 否则，它将为的子节点**其他语言**。  
  
##### <a name="folder"></a>文件夹  
 如果存在此子项，则根节点将成为指定的文件夹的子节点。 在项下将显示可能的文件夹的列表  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 例如，该数据库项目项具有与其他项目类型条目中 PseudoFolders 文件夹密钥。 因此，在**项目类型**树中，**数据库项目**将作为子节点的**其他项目类型**。  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>项目类型子节点和.vstdir 文件  
 中的子节点的位置**项目类型**树遵循 ProjectTemplates 文件夹中文件夹的层次结构。 机模板 (**Visual Studio 已安装的模板**)，典型位置是 files\microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ 和用户模板 (**我模板**)，典型位置是 documents\visual Studio 14.0\Templates\ProjectTemplates\\。 从这两个位置的文件夹层次结构合并，以创建**项目类型**树。  
  
 对 C# 开发人员设置，Visual Studio**项目类型**树看上去如下所示：  
  
 ![项目类型](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 相应的 ProjectTemplates 文件夹类似如下所示：  
  
 ![项目模板](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 当**新项目**对话框随即打开，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]遍历 ProjectTemplates 文件夹并重新创建在其结构**项目类型**具有一些更改树：  
  
-   中的根节点**项目类型**树由应用程序模板。  
  
-   节点名称可以本地化，且可包含特殊字符。  
  
-   可以更改排序顺序。  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>对于项目类型中查找的根节点  
 当 Visual Studio 遍历 ProjectTemplates 文件夹时，打开所有.zip 文件，并提取任何.vstemplate 文件。 .Vstemplate 文件使用 XML 来描述应用程序模板。 有关详细信息，请参阅[新项目生成： 高级选项、 第二](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。  
  
 \<ProjectType > 标记确定应用程序的项目类型。 例如，\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 文件包含一个具有此标记的 EmptyProject.vstemplate 文件：  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > 标记中，并且不在 ProjectTemplates 文件夹中，子文件夹确定中的应用程序的根节点**项目类型**树。 在示例中，Windows CE 应用程序将出现在下**Visual C#**根节点下，即使你是将 WindowsCE 文件夹移到 VisualBasic 文件夹，Windows CE 应用程序仍将出现在**Visual C#**根节点。  
  
##### <a name="localizing-the-node-name"></a>本地化的节点名称  
 当 Visual Studio 遍历 ProjectTemplates 文件夹时，它将检查它找到的任何.vstdir 文件。 .Vstdir 文件是一个 XML 文件，用于控制中的项目类型的外观**新项目**对话框。 在.vstdir 文件中，使用\<LocalizedName > 标记添加到名称**项目类型**节点。  
  
 例如，\CSharp\Database\TemplateIndex.vstdir 文件包含此标记：  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 这将确定在这种情况下，命名的根节点，则本地化字符串的附属 DLL 和资源 ID**数据库**。 本地化的名称可以包含特殊字符，如将不可用的文件夹名称**.NET**。  
  
 如果没有\<LocalizedName > 标记，该文件夹本身，命名该项目类型**SmartPhone2003**。  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>查找项目类型的排序顺序  
 若要确定项目类型的排序顺序，.vstdir 文件使用\<SortOrder > 标记。  
  
 例如，\CSharp\Windows\Windows.vstdir 文件包含此标记：  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir 文件具有一个标记具有更大的值：  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 中的较小数字\<SortOrder > 标记越高的位置、 在树中，因此**Windows**节点显高于**数据库**中的节点**项目类型**树。  
  
 如果没有\<SortOrder > 标记指定对于项目类型，它将出现在以下任何项目类型包含的字母顺序\<SortOrder > 规范。  
  
 请注意在我的文档没有.vstdir 文件 (**我的模板**) 文件夹。 用户应用程序项目类型名称未本地化，且按字母顺序显示。  
  
#### <a name="a-quick-review"></a>快速查看  
 让我们修改**新项目**对话框框中，并创建新用户项目模板。  
  
1.  将 MyProjectNode 子文件夹添加到 files\microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp 文件夹。  
  
2.  使用任何文本编辑器的 MyProjectNode 文件夹中创建 MyProject.vstdir 文件。  
  
3.  将这些行添加到.vstdir 文件：  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  保存并关闭.vstdir 文件。  
  
5.  使用任何文本编辑器的 MyProjectNode 文件夹中创建 MyProject.vstemplate 文件。  
  
6.  将这些行添加到.vstemplate 文件：  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  保存 the.vstemplate 文件并关闭编辑器。  
  
8.  将.vstemplate 文件发送到新的压缩 MyProjectNode\MyProject.zip 文件夹。  
  
9. 从 Visual Studio 命令窗口中，键入：  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 打开 Visual Studio。  
  
1.  打开**新项目**对话框框中，展开**Visual C#**项目节点。  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode**显示为一个子节点的 Visual C# Windows 节点的正下方。  
  
## <a name="see-also"></a>另请参阅  
 [生成新项目：揭秘，第 2 部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)