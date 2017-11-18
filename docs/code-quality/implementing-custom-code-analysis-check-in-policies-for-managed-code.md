---
title: "实现自定义代码分析签入策略的托管代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c2853d06bf7dcf2ffd894ee3ae1a90e78e61c6d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>对托管代码实施自定义代码分析签入策略
代码分析签入策略指定到版本控制签入前，团队项目的成员必须在源代码运行的规则的一组。 Microsoft 提供了一套标准*规则集*该组代码分析规则到功能区域。 *自定义签入策略规则集*指定一组特定于团队项目的代码分析规则。 规则集存储在的.ruleset 文件中。  
  
 签入策略是在团队项目级别设置，并且指定的版本控制树中的.ruleset 文件位置。 没有版本控制的位置的团队策略自定义规则集限制。  
  
 为每个项目的属性窗口中的单个代码项目配置了代码分析。 自定义规则为代码项目设置指定的.ruleset 文件在本地计算机上的物理位置。 如果所指定的 .ruleset 文件位于代码项目所在的驱动器上，则 Visual Studio 将在项目配置中使用文件的相对路径。  
  
 用于创建团队项目自定义规则集的建议的做法是在不属于任何代码项目的特殊文件夹中存储的签入策略.ruleset 文件。 如果将文件存储在专用文件夹，你可以应用权限来限制哪些人可以编辑该规则文件，并且你可以轻松地将目录结构，包含到另一个目录或计算机的项目。  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>创建团队项目签入的自定义规则集  
 若要创建自定义规则为团队项目设置，请首先创建签入策略中的规则集特殊文件夹**源代码管理器**。 创建规则集文件，并将文件添加到版本控制。 最后，你指定将设置为代码分析签入策略为团队项目的规则。  
  
> [!NOTE]
>  若要创建的团队项目中的文件夹，你首先必须映射团队项目根目录到本地计算机上的位置。 有关详细信息，请参阅[创建和使用工作区 （旧）](http://msdn.microsoft.com/en-us/db4d5692-179a-44fe-ad31-0c1c900c9cb2)。  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>若要创建签入策略规则集的版本控制文件夹  
  
1.  在[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]，展开该团队项目节点，，然后单击**源代码管理**。  
  
2.  在**文件夹**窗格中，右键单击团队项目，然后单击**新文件夹**。  
  
3.  在主源代码管理窗格中，右键单击**新文件夹**，单击**重命名**，并键入规则集文件夹的名称。  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>若要创建签入策略规则设置  
  
1.  上**文件**菜单上，指向**新建**，然后单击**文件**。  
  
2.  在**类别**列表中，单击**常规**。  
  
3.  在**模板**列表中，双击**代码分析规则集**。  
  
4.  指定要包括在规则集中的规则，然后将规则集文件保存到你创建的规则集文件夹。  
  
     有关详细信息，请参阅[创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>若要将规则添加到版本控制设置文件  
  
1.  在**源代码管理器**，右键单击新文件夹，，然后单击**将项添加到文件夹**。  
  
     有关详细信息，请参阅[使用版本控制](http://msdn.microsoft.com/Library/33267cee-fe5f-4aa3-b2cd-6d22ceace314)。  
  
2.  单击该规则设置你创建文件，然后单击**完成**。  
  
     该文件是添加到源代码管理，并为您签出。  
  
3.  在**源代码管理器**详细信息窗口中，右键单击的文件名称，然后单击**签入挂起的更改**。  
  
4.  在**签入**对话框中，你可以选择添加注释，然后单击**签入**。  
  
    > [!NOTE]
    >  如果你已为你的团队项目配置代码分析签入策略，并且选择了**执行签入以只包含属于当前解决方案的文件**，则将触发策略失败警告。 在策略失败对话框中，选择**重写策略失败，并继续签入**。 添加所需的注释，，然后单击**确定**。  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>若要指定的规则设置文件，为签入策略  
  
1.  上**团队**菜单上，指向**团队项目设置**，然后单击**源代码管理**。  
  
2.  单击**签入策略**，然后单击**添加**。  
  
3.  在**签入策略**列表中，双击**代码分析**，并确保**适用于托管代码强制实施代码分析**复选框处于选中状态。  
  
4.  在**运行此规则集**列表中，单击**\<从源代码管理选择规则集 >**。  
  
5.  键入在版本控制中签入策略规则集文件的路径。  
  
     路径必须符合以下语法：  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  你可以通过使用中的以下过程之一来复制路径**源代码管理器**:  
  
    -   在**文件夹**窗格中，单击包含规则集文件的文件夹。 将复制的文件夹中显示的版本控制路径**源**框，然后手动键入规则集文件的名称。  
  
    -   在详细信息窗口中，右键单击规则集文件，并依次**属性**。 上**常规**选项卡上，复制中的值**服务器名称**。  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>同步到签入策略规则集的代码项目  
 指定团队项目签入策略规则集的代码项目的属性对话框中的代码项目配置的代码分析规则集。 如果代码项目所在的驱动器上位于规则集，则相对路径用于指定规则集时的路径从文件对话框中选择。 使用相对路径，可移植到其他计算机使用类似的本地版本的项目属性设置控制结构。  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>若要指定团队项目规则设置为代码项目规则集  
  
1.  如有必要，检索从版本控制签入策略规则集文件夹和文件。  
  
     你可以执行此步骤在**源代码管理器**通过右键单击该规则设置文件夹，然后单击**获取最新版本**。  
  
2.  在**解决方案资源管理器**，右键单击代码项目，然后单击**属性**。  
  
3.  **单击代码分析**。  
  
4.  如有必要，单击中的相应选项**配置**和**平台**列出。  
  
5.  若要使用指定的配置生成的代码项目时每次运行代码分析，选择**启用生成代码分析 （定义 CODE_ANALYSIS 常量）**复选框。  
  
6.  若要忽略从其他公司的组件中的代码，请选择**禁止显示生成代码产生的结果**复选框。  
  
7.  在**运行此规则集**列表中，单击**\<浏览 … >**。  
  
8.  指定的本地版本的签入策略规则集文件。