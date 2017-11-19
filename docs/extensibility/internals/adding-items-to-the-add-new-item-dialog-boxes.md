---
title: "将项添加到添加新项对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a16698863e92e5bbae4e888502788dd76b04f56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>将项添加到添加新项对话框
将项添加到的过程**添加新项**对话框开头的注册表项。 下列注册表项中所示，AddItemTemplates 部分包含的路径和名称在中可用的项中的目录**添加新项**放对话框。  
  
> [!NOTE]
>  紧跟在代码段的表包含有关注册表项的其他信息。  
  
 本部分位于 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects] 下。  
  
 第一个 GUID 是此类型; 的项目的 CLSID第二个 GUID 指示添加项模板的已注册的项目类型。  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir"="\<Visual Studio SDK 安装路径\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority"= dword:00000064  
  
|名称|类型|数据 （来自.rgs file)|描述|  
|----------|----------|-----------------------------|-----------------|  
|@ （默认值）|REG_SZ|#%IDS_ADDITEM_TEMPLATES_ENTRY %|资源 ID**添加项**模板。|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\SomeProjectItems|在对话框中显示的项目项路径**添加新项**向导。|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|确定显示在文件的树节点中的排序顺序**添加新项**对话框。|  
  
> [!NOTE]
>  Visual C# 和 Visual Basic 项目类型的 GUID 如下所示：[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 所列出的目录的左侧节点 TemplateDirs，即 %template_path%\someprojectitems 为**添加新项**对话框框树。 在树中的其他元素基于内该根目录的子目录。 可用于添加到项目文件是在右窗格中的项**添加新项**对话框。  
  
 通常情况下，此文件夹将包含如模板 HTML 或.cpp 文件中，你的项目的模板文件并启动向导的任何.vsz 文件。 若要控制项的显示方式，还可以包括.vsdir 本地化目录名称和图标的文件。 本地化的字符串是表示添加新项对话框树中的此节点的对话框中显示的标题。  
  
 但是，不需要一个.vsdir 文件中包含的所有内容。 你可以有.vsdir 文件的目录中的每个项。 有关详细信息，请参阅[向导 (。Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)和[模板目录说明 (。Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
> [!NOTE]
>  中的模板目录的.vsdir 文件是可选的。 如果你只想要将置于目录中的项目元素并将其显示在**添加新项**对话框中，可以将此文件放在 TemplatesDir 语句中指定的模板目录中。 该文件将显示在右窗格中**添加新项**对话框中为该项目。 但是，如果你想要显示本地化的标题文件或一个图标，你必须包含至少一个.vsdir 文件模板目录中。  
  
## <a name="grouping-project-items"></a>分组项目项  
 如果你想要包含在文件夹中的模板组**添加新项**对话框框树中，你必须使用的项目的根模板目录下的子目录中。 当**添加新项**向用户显示对话框中，它们将还查看文件夹以及能够从中选择项目元素。  
  
 在代码段的排序优先级确定将其中中相对于其他元素的树节点的树中创建此模板目录。 有关**添加新项**对话框中，排序优先级是所有你必须包括，以便你的项将显示在对话框中的正确位置。  
  
 你也可以实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>接口来筛选中显示的内容**添加新项**对话框。 通过实现此接口，你可以将设置一个模板目录包含，例如，磁盘上 50 个模板和向导文件。 以这种方式，你可以使用 20 个属于一个项目类型、 属于其他项目类型，其他 30 文件和常规类型的项目中可用的所有文件的文件的不同项目类型。 在这种方式，具体取决于哪些项目创建模板，你可以显示一组不同的模板文件。  
  
 例如，在 Visual Basic 项目中，您可能 Web 项目和客户端项目。 Web 窗体不是有用的项将添加到客户端项目，且 windows 窗体不是有用的项将添加到 Web 服务器项目。 因此，你可以创建一个包含两种类型的项目的所有文件的模板目录。 然后通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>，您可以隐藏不应显示基于项目或项目中的项目设置的类型的项目。  
  
## <a name="filtering-project-items"></a>筛选的项目项  
 `IVsFilterAddProjectItemDlg2`提供用于通过以下方式筛选树 （左窗格中） 和项目文件 （右窗格） 中的元素：  
  
-   本地化的名称 （.vsdir 文件中包含的对话框中显示的标题） 通过提供`IVsFilterAddProjectItemDlg`。  
  
-   通过文件和文件夹在磁盘上的实际名称 (非本地化-没有.vsdir 文件) 提供的`IVsFilterAddProjectItemDlg`。  
  
-   按类别，提供`IVsFilterAddProjectItemDlg2`。  
  
 若要按类别筛选，请提供.vsdir 文件，如"Web 窗体"中的项或在 Visual Basic 中的"客户端项"的类别字符串。 然后，对话框代码从.vsdir 文件中检索类别分类，并将其传递给你。 然后，你可以将该信息传递到的实现`IVsFilterAddProjectItemDlg2`来筛选**添加新项**对话框中按类别。 对 Web 页或与客户端 Win32 应用程序用例，你还可以筛选项。 此外，你可以标识[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]标记为 Microsoft 基础类 (MFC) 或活动模板库 (ATL) 项的项。 如果确定这些项，项目系统可以定义自己分类，以便系统可以根据类别和分类筛选。  
  
 如果你实现此筛选器功能，你不需要映射应隐藏的每个项的表。 你只需对项进行分类为类型并置于.vsdir 文件或文件的分类。 然后您可以隐藏所有通过实现该接口具有特定分类的项。 在这种方式，可以进行中的项**添加新项**对话框框中动态基于项目中的状态。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [通常用于扩展项目的对象的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [模板目录说明 (。Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [向导 (.Vsz) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)