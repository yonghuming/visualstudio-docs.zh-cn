---
title: "将项添加到添加新项对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "添加新项对话框，添加项"
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 将项添加到添加新项对话框
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将项添加到的过程 **添加新项** 对话框开头的注册表项。 以下注册表项中所示，AddItemTemplates 部分包含的路径和名称中提供哪些项中的目录 **添加新项** 放入对话框。  
  
> [!NOTE]
>  紧随的代码段的表包含有关该注册表项的其他信息。  
  
 本部分位于 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0Exp\\Projects\] 下。  
  
 首个 GUID 是此类型; 的项目的 CLSID第二个 GUID 指示添加的项模板的已注册的项目类型。  
  
 \\{C061DB26\-5833\-11D2\-96F5\-000000000000}\\AddItemTemplates\\TemplateDirs\\ {ACEF4EB2\-57CF\-11D2\-96F4\-000000000000} \\1  
  
 @\="\#6"  
  
 "TemplatesDir"\="\< Visual Studio SDK 安装 path\\\\VSIntegration\\\\SomeFolder\\\\SomePackage\\\\SomeProject\\\\SomeProjectItems"  
  
 "SortPriority"\= dword:00000064  
  
|名称|类型|\(.Rgs 文件\) 中的数据|说明|  
|--------|--------|----------------------|--------|  
|@ \(默认值\)|REG\_SZ|\#%IDS\_ADDITEM\_TEMPLATES\_ENTRY %|资源 ID **添加项** 模板。|  
|Val TemplatesDir|REG\_SZ|%TEMPLATE\_PATH%\\SomeProjectItems|显示的对话框中的项目项的路径 **添加新项** 向导。|  
|Val SortPriority|REG\_DWORD|100 \([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]\)|确定文件中显示的树节点中的排序顺序 **添加新项** 对话框。|  
  
> [!NOTE]
>  对于 Visual C\# 和 Visual Basic 项目类型的 GUID 如下所示:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F}  
  
 所列出的目录的左侧节点 TemplateDirs，即 %template\_path%\\someprojectitems 为 **添加新项** 对话框框中的树。 在树中的其他元素都基于在该根目录的子目录。 可供添加到项目文件是在右窗格中的项 **添加新项** 对话框。  
  
 通常情况下，此文件夹将包含如模板 HTML 或.cpp 文件中，您的项目的模板文件和任何.vsz 文件来启动向导。 若要控制项的显示方式，还可以包括.vsdir 文件用于本地化的目录名称和图标。 本地化的字符串是显示在对话框中，表示此节点在树中添加新项对话框的标题。  
  
 但是，不需要在一个.vsdir 文件中具有的所有内容。 您可以在目录中的每个项的一个.vsdir 文件。 有关详细信息，请参阅 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md) 和 [模板目录说明 \(。Vsdir\) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
> [!NOTE]
>  模板目录中的.vsdir 文件是可选的。 如果只是想要放入目录中的项目元素，并将其显示在 **添加新项** 对话框中，可以将此文件放在 TemplatesDir 语句中指定的模板目录中。 该文件将显示在右窗格中 **添加新项** 对话框中为该项目。 但是，如果您想要显示的本地化的标题文件或图标，您必须包含至少一个.vsdir 文件模板目录中。  
  
## 分组项目项  
 如果你想要包含在文件夹中的模板组 **添加新项** 对话框框中树中，则必须使用的项目模板根目录下的子目录中它们。 当 **添加新项** 向用户显示对话框，它们还将查看子文件夹，并可以从中选择项目元素。  
  
 代码段中的排序优先级确定将其中在相对于其他元素的树节点树中创建此模板目录。 有关 **添加新项** 对话框中的排序优先级是所有必须包括以便您的项目将显示在对话框中的正确位置。  
  
 您还可以实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 接口，以筛选器中显示的内容 **添加新项** 对话框。 通过实现此接口，您可以设置模板目录包含，例如，磁盘上 50 个模板和向导文件。 这种方式，您可以与属于一个项目类型、 其他 30 文件属于另一个项目类型，以及常规类型的项目中可用的所有文件的 20 个文件的不同项目类型。 在这种方式，具体取决于哪个项目创建模板，可以显示一组不同的模板文件。  
  
 例如，在 Visual Basic 项目中，可能有 Web 项目和客户端项目。 Web 窗体不是很有用的项将添加到客户端项目和 windows 窗体不是很有用的项将添加到 Web 服务器项目。 因此，您可以创建一个包含两种类型的项目的所有文件的模板目录。 然后通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, ，您可以隐藏不应显示基于项目或项目中的项目设置的类型的项目。  
  
## 筛选的项目项  
 `IVsFilterAddProjectItemDlg2` 提供了以下列方式筛选树 \(左窗格中\) 和项目文件 \(右窗格\) 中的元素:  
  
-   本地化的名称 \(.vsdir 文件中包含的对话框中显示的标题\) 通过提供 `IVsFilterAddProjectItemDlg`。  
  
-   通过文件和磁盘上的文件夹的实际名称 \(非本地化 — 没有.vsdir 文件\) 提供的 `IVsFilterAddProjectItemDlg`。  
  
-   按类别、 由 `IVsFilterAddProjectItemDlg2`。  
  
 若要按类别筛选，请提供连接到某个项在.vsdir 文件中，如"Web 窗体"或"客户端 item"\(在 Visual Basic 中的类别字符串。 然后，对话框代码从.vsdir 文件中检索类别分类，并将其传递给您。 然后可以将该信息传递给您实现 `IVsFilterAddProjectItemDlg2` 筛选 **添加新项** 按类别的对话框。 用于 Web 页或用作客户端 Win32 应用程序的情况下，还可以筛选项。 此外，您可以标识 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 标记为 Microsoft 基础类 \(MFC\) 或多个活动模板库 \(ATL\) 项目的项。 时识别出这些项，项目系统可以定义自己的分类，以便可以根据类别和分类筛选系统。  
  
 如果实现此筛选器功能，您无需映射的表应隐藏每一项。 只需对项目进行分类为类型并将分类放.vsdir 文件或文件中。 然后您可以隐藏所有通过实现该接口有某个特定分类中的项。 在这种方式，可以进行中的项 **添加新项** 对话框框中动态基于项目中的状态。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [通常用于扩展项目的对象的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [模板目录说明 \(。Vsdir\) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)