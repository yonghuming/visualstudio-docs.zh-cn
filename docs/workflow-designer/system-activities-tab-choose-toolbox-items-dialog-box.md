---
title: "System.Activities 选项卡上，选择工具箱项对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc005e282e7581aa2af5cba7da3a23040bf9d8b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>“System.Activities”选项卡 ->“选择工具箱项”对话框
此选项卡**选择工具箱项**对话框中显示的列表[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]活动、 模板和项提供给你。 若要显示此列表，选择**选择工具箱项**从**工具**菜单或通过右击**工具箱**并选择**选择项**以显示**选择工具箱项**对话框中，然后选择其**System.Activities**选项卡。在初始状态下，该列表包含 System.Activities、 System.ServiceModel.Activities 和 System.Activities.Core.Presentation 程序集; 的工作流活动但是，仅系统提供显示的活动和活动通过显示在其他程序集添加**工具箱**默认选中。 新添加的活动会自动选中，并显示在**工具箱**单击**确定**在对话框中。 此外，这些项显示在**工具箱**对应于活动/项/模板所在的命名空间的新类别下。  
  
> [!WARNING]
>  如果您试图添加未包含任何工作流活动的程序集，则将显示一个错误对话框，指出该程序集没有包含任何活动。  
  
 此对话框是项目不可知的因而**System.Activities**选项卡继续显示在独立的 XAML 或非工作流项目类型。  
  
 对每个选项卡都会执行筛选。这意味着不能添加工作流活动通过**.NET 组件**选项卡。他们需要通过添加**System.Activities**选项卡本身。  
  
 你可以取消选中不希望若要查看在任何的项**工具箱**从该对话框选项卡上，或或者，你可以使用来完成**删除**中的上下文菜单选项**工具箱**取消引用程序集不会删除的项和**工具箱**。  
  
 通过将活动拖放到设计器上来实例化该活动会自动将包含该项的程序集添加到引用的程序集列表中。 此外，如果该活动引用程序集 C，它不会将 C 添加到引用的程序集列表中。 程序集 C 必须在 GAC 中或与活动 B.相同的目录在独立事例中，程序集必须在 GAC 中或 VS 的 Probe 路径。 只有在那时，您可以拖动和删除工作流设计器图面上的活动。  
  
 **工具箱**设置默认保存为用户选项，因此下一步的时间，当你打开**工具箱**，它将显示你自定义工作流活动的列表。 这样的一个副作用是，如果你已添加到将特定域项**工具箱**通过**选择工具箱项**对话框中，你仍然继续查看当你使用的那些项工作流控制台应用程序以及。 如果你不希望以查看它们，然后删除它们使用上下文菜单或取消选中它们通过**选择工具箱项**对话框中，如前面所述。  
  
 此对话框中的列包含以下信息：  
  
 名称  
 列出当前已在您的本地计算机上注册的工作流活动的名称。  
  
 命名空间  
 显示定义活动结构的 .NET Framework 类库命名空间的层次结构。  
  
 程序集名称  
 显示包含活动的 .NET Framework 程序集的名称和版本。  
  
 目录  
 显示包含工作流活动的 .NET Framework 程序集的位置。 所有程序集的默认位置是全局程序集缓存。  
  
 若要对所列组件排序，请选择任意列标题。