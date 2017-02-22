---
title: "“System.Activities”选项卡 -&gt;“选择工具箱项”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS"
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS"
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# “System.Activities”选项卡 -&gt;“选择工具箱项”对话框
**“选择工具箱项”**对话框的此选项卡显示可用的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 活动、模板和项的列表。若要显示此列表，请从**“工具”**菜单中选择**“选择工具箱项”**，或右击**“工具箱”**并选择**“选择项”**，从而显示**“选择工具箱项”**对话框，然后选择其中的**“System.Activities”**选项卡。该列表包含 System.Activities、System.ServiceModel.Activities 和 System.Activities.Core.Presentation 程序集中现成可用的工作流活动；但默认情况下仅选中**“工具箱”**中显示的系统提供的活动和“工具箱”中显示的通过其他程序集添加的活动。最新添加的活动会自动选中，并在您单击该对话框上的**“确定”**时显示在**“工具箱”**中。此外，这些项显示在**“工具箱”**中与活动\/项\/模板所驻留的命名空间对应的新类别下。  
  
> [!WARNING]
>  如果您试图添加未包含任何工作流活动的程序集，则将显示一个错误对话框，指出该程序集没有包含任何活动。  
  
 此对话框是项目不可知的，因此**“System.Activities”**选项卡将继续以独立 XAML 或非工作流项目类型显示。  
  
 对每个选项卡都会执行筛选。这意味着无法通过**“.NET 组件”**选项卡添加工作流活动。必须通过**“System.Activities”**选项卡本身添加工作流活动。  
  
 通过此对话框选项卡可以取消选中不希望在**“工作箱”**中看到的任何项，使用**“工具箱”**中的**“删除”**上下文菜单选项也可以达到此目的，但取消引用某个程序集不会从**“工具箱”**中移除相应项。  
  
 通过将活动拖放到设计器上来实例化该活动会自动将包含该项的程序集添加到引用的程序集列表中。此外，如果该活动引用程序集 C，它不会将 C 添加到引用的程序集列表中。必须是 GAC 或活动 B 相同的目录中的程序集 C。在独立事例中，程序集必须是 GAC 或 VS 的探针路径中。只有到那时可以拖动并删除工作流设计器图面上的活动。  
  
 默认情况下，**“工具箱”**设置保存为用户选项，因此当您下次打开**“工作箱”**时，其中将显示您的自定义工作流活动列表。这样做的一个缺点在于，如果已通过**“选择工具箱项”**对话框将特定域项添加到**“工具箱”**中，则在工作流控制台应用程序中工作时仍能看见那些项。如果不希望看到那些项，则可按前面所述使用上下文菜单或通过在**“选择工作箱项”**对话框中取消选中那些项来删除它们。  
  
 此对话框中的列包含以下信息：  
  
 Name  
 列出当前已在您的本地计算机上注册的工作流活动的名称。  
  
 命名空间  
 显示定义活动结构的 .NET Framework 类库命名空间的层次结构。  
  
 程序集名称  
 显示包含活动的 .NET Framework 程序集的名称和版本。  
  
 目录  
 显示包含工作流活动的 .NET Framework 程序集的位置。所有程序集的默认位置是全局程序集缓存。  
  
 若要对所列组件排序，请选择任意列标题。