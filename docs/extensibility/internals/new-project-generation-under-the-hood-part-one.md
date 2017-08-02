---
title: "生成新的项目︰ 实质上，第 1 部分 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio]，新建项目对话框"
  - "项目 [Visual Studio]，新项目生成"
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 生成新的项目︰ 实质上，第 1 部分
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

是否曾经想过如何创建您自己的项目类型？ 想知道实际情况时创建一个新项目？ 让我们了解一下在底层，看什么真正的进展。  
  
 有几个 Visual Studio 协调为您的任务︰  
  
-   它将显示所有可用的项目类型的树。  
  
-   它显示每种项目类型的应用程序模板的列表，并允许您选择其中一项。  
  
-   它收集应用程序，例如项目名称和路径的项目信息。  
  
-   它将此信息传递到项目工厂。  
  
-   它生成当前解决方案中的项目项和文件夹。  
  
## 新项目对话框中  
 所有它将开始时选择一个新的项目的项目类型。 首先，通过单击 **新项目** 上 **文件** 菜单。**新项目** 出现对话框，外观如下所示︰  
  
 ![“新建项目”对话框](~/extensibility/internals/media/newproject.gif "NewProject")  
  
 让我们仔细看。**项目类型** 树列出了您可以创建的各种项目类型。 当选择项目类型，如 **Visual C\# Windows**, ，您将看到应用程序模板帮助您入门的列表。**Visual Studio 已安装的模板** Visual Studio 安装并可供您的计算机的任何用户。 创建或收集的新模板可以添加到 **我的模板** 并且仅提供给你。  
  
 当选择模板与相似 **Windows 应用程序**, ，应用程序类型的说明将显示在对话框中，在这种情况下， **用于与 Windows 用户界面创建应用程序的项目**。  
  
 在底部 **新项目** 对话框中，您将看到收集的详细信息的多个控件。 您看到的控件取决于项目类型，但它们通常包括一个项目 **名称** 文本框中， **位置** 文本框及相关 **浏览** 按钮，和一个 **解决方案名称** 文本框及相关 **创建解决方案的目录** 复选框。  
  
## 填充新项目对话框中  
 其中未 **新项目** 对话框获取从其信息？ 在工作在这里，至少不推荐使用的其中一个有两种机制。**新项目** 对话框将合并，并显示从这两种机制获取的信息。  
  
 较旧的 （已弃用） 方法使用系统注册表项和.vsdir 文件。 Visual Studio 打开时，将运行此机制。 较新的方法使用.vstemplate 文件。 在 Visual Studio 在初始化时，例如，通过运行时运行此机制  
  
```  
devenv /setup  
```  
  
 或  
  
```  
devenv /installvstemplates  
```  
  
### 项目类型  
 位置和名称 **项目类型** 根节点，如 **Visual C\#** 和 **其他语言**, ，由系统注册表项。 组织这些子节点，如 **数据库** 和 **智能设备**, ，镜像包含相应的.vstemplate 文件的文件夹层次结构。 让我们看一下的根节点，第一次。  
  
#### 项目类型的根节点  
 当 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是初始化，遍历系统注册表项 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0\\NewProjectTemplates\\TemplateDirs 若要生成和名称的根节点的子项 **项目类型** 树。 此信息缓存供以后使用。 看看 TemplateDirs\\ {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC} \\\/1 键。 每个条目为 VSPackage 的 GUID。 该子项的名称 （\/ 1） 将被忽略，但它的存在表明这是 **项目类型** 根节点。 根节点反过来会因多个控件中的外观的子项 **项目类型** 树。 让我们看一下其中一些。  
  
##### \(默认\)  
 这是名称的根节点的本地化字符串的资源 ID。 字符串资源都位于附属 DLL 选择的 VSPackage GUID。  
  
 在示例中，是 VSPackage GUID  
  
 {} FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC  
  
 根节点的资源 ID （默认值） 和 （\/ 1） 是 \# 2345年  
  
 如果您查找附近的包项中的 GUID，并检查 SatelliteDll 子项，您可以找到包含字符串资源的程序集的路径︰  
  
 \< visual Studio 安装路径 \> \\VC\#\\VCSPackages\\1033\\csprojui.dll  
  
 若要验证这一点，打开文件资源管理器，并将 csprojui.dll 拖入 Visual Studio 目录... 字符串表显示了资源 \# 2345年带有题注 **Visual C\#**。  
  
##### SortPriority  
 这可确定的位置中的根节点 **项目类型** 树。  
  
 SortPriority REG\_DWORD 0x00000014 \(20\)  
  
 优先级越低编号树中的较高位置。  
  
##### DeveloperActivity  
 如果存在此子项，则由开发人员设置对话框中控制的根节点的位置。 例如，  
  
 DeveloperActivity REG\_SZ VC \#  
  
 指示 Visual C\# 将根节点是否 Visual Studio 设置为 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 开发。 否则，它将作为子节点的 **其他语言**。  
  
##### 文件夹  
 如果存在此子项，则根节点将成为指定的文件夹的子节点。 在项下出现的可能的文件夹列表  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\NewProjectTemplates\\PseudoFolders  
  
 例如，数据库项目条目都具有文件夹匹配的键的 PseudoFolders 中的其他项目类型条目。 因此，在 **项目类型** 树中， **数据库项目** 将作为子节点的 **其他项目类型**。  
  
#### 项目类型的子节点和.vstdir 文件  
 中的子节点的位置 **项目类型** 树遵循 ProjectTemplates 文件夹中文件夹的层次结构。 机模板 \(**Visual Studio 已安装的模板**\)，典型位置是 files\\microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\ 和用户模板 \(**我的模板**\)，典型位置是 documents\\visual Studio 14.0\\Templates\\ProjectTemplates\\。 从这两个位置的文件夹层次结构进行合并，以创建 **项目类型** 树。  
  
 对 C\# 开发人员设置，Visual Studio **项目类型** 树看上去如下所示︰  
  
 ![项目类型](~/extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 如下所示的相应 ProjectTemplates 文件夹中︰  
  
 ![项目模板](~/extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 当 **新项目** 对话框将打开， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 遍历 ProjectTemplates 文件夹，并重新创建其结构处于 **项目类型** 树中的某些更改︰  
  
-   中的根节点 **项目类型** 树由应用程序模板。  
  
-   节点名称可以本地化，且可包含特殊字符。  
  
-   可以更改排序顺序。  
  
##### 一种项目类型中查找根节点  
 当 Visual Studio 遍历 ProjectTemplates 文件夹时，打开所有.zip 文件，并提取任何.vstemplate 文件。 .Vstemplate 文件使用 XML 来描述应用程序模板。 有关详细信息，请参阅[生成新的项目: 实质上，第二部分](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)。  
  
 \< ProjectType \> 标记确定该应用程序的项目类型。 例如，\\CSharp\\SmartDevice\\WindowsCE\\1033\\WindowsCE\-EmptyProject.zip 文件包含一个具有此标记的 EmptyProject.vstemplate 文件︰  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \< ProjectType \> 标记中，并且不 ProjectTemplates 文件夹中的子文件夹确定应用程序中的根节点 **项目类型** 树。 在示例中，Windows CE 应用程序将出现在下 **Visual C\#** 根节点，并且即使您打算将 WindowsCE 文件夹移动到 VisualBasic 文件夹，Windows CE 应用程序仍将显示在下 **Visual C\#** 根节点。  
  
##### 本地化的节点名称  
 当 Visual Studio 遍历 ProjectTemplates 文件夹时，它将检查它找到的任何.vstdir 文件。 .Vstdir 文件是一个 XML 文件，用于控制中的项目类型的外观 **新项目** 对话框。 在.vstdir 文件中，使用 \< LocalizedName \> 标记添加到名称 **项目类型** 节点。  
  
 例如，\\CSharp\\Database\\TemplateIndex.vstdir 文件包含此标记︰  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 这可确定在这种情况下，命名根节点的本地化字符串的附属 DLL 和资源 ID **数据库**。 本地化的名称可包含特殊字符所没有的文件夹名称，如 **.NET**。  
  
 如果存在没有 \< LocalizedName \> 标记，则按文件夹本身，命名项目类型 **SmartPhone2003**。  
  
##### 查找项目类型的排序顺序  
 若要确定项目类型的排序顺序，.vstdir 文件，请使用 \< SortOrder \> 标记。  
  
 例如，\\CSharp\\Windows\\Windows.vstdir 文件包含此标记︰  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \\CSharp\\Database\\TemplateIndex.vstdir 文件都有具有较大的值的标记︰  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 \< SortOrder \> 中的数字越小标记，更高版本的位置在树中，因此 **Windows** 节点显高于 **数据库** 中的节点 **项目类型** 树。  
  
 如果为一种项目类型指定没有 \< SortOrder \> 标记，则它将显示以下包含 \< SortOrder \> 规范任何项目类型的按字母顺序。  
  
 请注意在我的文档中没有.vstdir 文件 \(**我的模板**\) 文件夹。 用户应用程序项目类型名称未本地化，且按字母顺序显示。  
  
#### 快速查看  
 让我们修改 **新项目** 对话框框中，并创建新的用户项目模板。  
  
1.  将 MyProjectNode 子文件夹添加到 files\\microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\CSharp 文件夹。  
  
2.  在使用任何文本编辑器 MyProjectNode 文件夹中创建 MyProject.vstdir 文件。  
  
3.  将这些行添加到.vstdir 文件︰  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  保存并关闭.vstdir 文件。  
  
5.  在使用任何文本编辑器 MyProjectNode 文件夹中创建 MyProject.vstemplate 文件。  
  
6.  将以下行添加到的.vstemplate 文件︰  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  保存 the.vstemplate 文件并关闭编辑器。  
  
8.  .Vstemplate 文件发送到新的压缩 MyProjectNode\\MyProject.zip 文件夹。  
  
9. 从 Visual Studio 命令窗口中，键入︰  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 打开 Visual Studio。  
  
1.  打开 **新项目** 对话框框中，展开 **Visual C\#** 项目节点。  
  
 ![MyProjectNode](~/extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** 显示为一个子节点的 Visual C\# Windows 节点的紧下方。  
  
## 请参阅  
 [生成新的项目: 实质上，第二部分](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)