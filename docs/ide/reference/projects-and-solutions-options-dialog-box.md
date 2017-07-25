---
title: "“选项”对话框 ->“项目和解决方案” | Microsoft Docs"
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: dc7a0c10390de67b56a83d2824224bed24125db0
ms.openlocfilehash: 9e34dc6bd0a876be15dccaff519d67a566022008
ms.contentlocale: zh-cn
ms.lasthandoff: 07/17/2017

---
# <a name="projects-and-solutions-options-dialog-box"></a>“选项”对话框 ->“项目和解决方案”

设置与项目和解决方案相关的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 行为。 要访问这些选项，请选择“工具 > 选项”，展开“项目和解决方案”，然后单击“常规”。

通过相同对话框中的“位置”选项卡设置项目和模板文件夹的默认路径。
  
> [!NOTE]
>  对话框中的可用选项以及显示的菜单命令的名称和位置可能与“帮助”中的描述不同，具体取决于您的当前设置或版本。 此帮助页是根据“常规开发设置”而编写的。 若要查看或更改设置，请在“工具”菜单上选择“导入和导出设置”。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="general-tab-options"></a>常规选项卡选项  
 
**轻型解决方案加载** 可减少在 IDE 中加载大型解决方案所需的时间和内存。 包含多个 C#、Visual Basic 或 C++ 项目的大型解决方案使用轻型解决方案加载可能会看到显著的性能优势。

- **让 Visual Studio 选择最适合我的解决方案的内容**：让 Visual Studio 根据解决方案的特征来自动确定是否应用轻型解决方案加载。
- **启用**：加载解决方案时将始终应用轻型解决方案加载。
- **禁用**：从不应用轻型解决方案加载。

有关详细信息，请参阅[优化 Visual Studio 启动时间](../optimize-visual-studio-startup-time.md#speed-up-solution-load)

**如果生成完成时出现错误，则始终显示错误列表**  
仅当项目无法生成时，在完成生成时将打开“错误列表”窗口。 将显示在生成过程中发生的错误。 如果清除此选项，则仍将发生错误，但在完成生成时窗口将不会打开。 默认情况下会启用此选项。  

**跟踪解决方案资源管理器中的活动项**  
当选中时，“解决方案资源管理器”将自动打开，活动项处于选中状态。 选定的项根据您在项目或解决方案中使用的不同文件或设计器中的不同组件而不同。 清除此选项后，“解决方案资源管理器”中的所选内容不会自动更改。 默认情况下会启用此选项。  

**显示高级生成配置**  
当选中时，生成配置选项显示在“项目属性页”对话框和“解决方案属性页”对话框中。 如果未选中，对于包含一个配置或两个配置调试和发布的 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目，生成配置选项将不显示在“项目属性页”对话框和“解决方案属性页”对话框中。 如果一个项目具有用户定义的配置，则会显示生成的配置选项。  

未选中时，“生成”菜单上的命令（如“生成解决方案”、“重新生成解决方案”和“清理解决方案”）将在发布配置上执行，“调试”菜单上的命令（如“启动调试”和“启动但不调试”）将在调试配置上执行。  

**总是显示解决方案**  
如果选中，该解决方案和解决方案中执行的所有命令将始终显示在 IDE 中。 未选中时，如果该解决方案只包含一个项目，所有项目将作为独立项目创建，您不会看到在解决方案资源管理器中的解决方案或 IDE 中解决方案的执行命令。  

**创建时保存新项目**  
当选中时，你可以在“新建项目”对话框中为你的项目指定位置。 如果未选中，所有新项目将创建为临时项目。 当您正在使用临时项目时，您可以创建和试验项目，无需指定磁盘位置。  

**当项目位置不受信任时警告用户**  
如果您尝试在不完全信任的位置（例如，在 UNC 路径或 HTTP 路径）创建一个新项目或打开现有项目，将显示一条消息。 使用此选项以指定每次在不完全受信任的位置尝试创建或打开一个项目时是否显示该消息。  

**在生成开始时显示输出窗口**  
在解决方案生成一开始就在 IDE 中自动显示输出窗口。 有关详细信息，请参阅[如何：控制输出窗口](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)。

**在重命名文件时提示重命名符号**  
选定后，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 将显示一个消息框，询问是否还应该将项目中的所有引用重命名为代码元素。  

**将文件移动到新位置之前显示提示**  
选定后，在通过解决方案资源管理器中的操作更改文件的位置之前，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 会显示确认消息框。 

## <a name="locations-tab-options"></a>位置选项卡选项

**项目位置**  
指定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在其中创建新的项目和解决方案文件夹的默认位置。 几个对话框还使用此选项中为文件夹起始点设置的位置。 例如，“打开项目”对话框将此位置用于“我的项目”的快捷方式。  

**用户项目模板位置**  
指定“新建项目”对话框中使用的默认位置来创建“我的模板”的列表。 有关详细信息，请参阅[如何：查找和组织模板](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。  

**用户项模板位置**  
指定“添加新项”对话框中使用的默认位置来创建“我的模板”的列表。 有关详细信息，请参阅[如何：查找和组织模板](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。 

## <a name="see-also"></a>另请参阅  
- [“选项”对话框 ->“项目和解决方案”->“生成和运行”](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- - [“选项”对话框、项目和解决方案、Web 项目](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
