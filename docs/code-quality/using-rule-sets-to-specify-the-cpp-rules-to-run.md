---
title: "使用规则集指定运行的 c + + 规则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5ad51388ae1580ada61442798b46048ad71ece64
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>使用规则集指定要运行的 C++ 规则
在[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]和[!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)]，您可以创建和修改自定义*规则集*以满足与代码分析相关联的特定项目需要。 若要创建自定义 C++ 规则集，必须在 Visual Studio IDE 中打开 C/C++ 项目。 然后，在规则集编辑器中打开某一标准规则集，再添加或移除特定的规则，并且可更改当代码分析确定违反规则时所发生的操作。  
  
 若要创建新的自定义规则集，使用新的文件名称保存它。 自定义规则集自动分配到项目。  
  
## <a name="opening-the-rule-set-editor"></a>打开该规则集编辑器  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>若要从单个的现有规则组中创建自定义规则  
  
1.  在解决方案资源管理器，打开项目的快捷菜单，然后选择**属性**。  
  
2.  上**属性**选项卡上，选择**代码分析**。  
  
3.  在**规则集**下拉列表中，执行下列其中一项：  
  
    -   选择要自定义的规则集。  
  
     \- 或 -  
  
    -   选择**\<浏览 … >**可以指定现有规则集不是在列表中。  
  
4.  选择**打开**若要在规则集编辑器中显示的规则。  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要修改的规则设置在规则集编辑器  
  
-   若要更改规则集的显示名称在**视图**菜单上，选择**属性窗口**。 输入中的显示名称**名称**框。 请注意，显示名称可以不同于文件名称。  
  
-   若要将组的所有规则都添加到自定义规则集，选择组的复选框。 若要删除的组的所有规则，请清除复选框。  
  
-   若要将特定规则添加到自定义规则集，请选择规则的复选框。 若要从规则集中删除规则，请清除复选框。  
  
-   若要更改的代码分析中违反规则时执行的操作，请选择**操作**字段规则，然后选择以下值之一：  
  
     **则发出警告**-生成一个警告。  
  
     **错误**-生成错误。  
  
     **无**-禁用规则。 此操作是从规则集内移除规则相同。  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>要进行分组，筛选，或者通过使用规则集编辑器工具栏更改规则集编辑器中的字段  
  
-   若要展开所有组中的规则，请选择**全部展开**。  
  
-   若要折叠所有组中的规则，请选择**全部折叠**。  
  
-   若要更改该规则按进行分组的字段，选择从字段**Group By**列表。 若要显示未分组的规则，请选择**\<无 >**。  
  
-   若要添加或删除字段在规则列中，选择**列选项**。  
  
-   若要隐藏不适用于当前解决方案的规则，请选择**隐藏不适用于当前解决方案的规则**。  
  
-   若要显示和隐藏分配了错误操作的规则之间切换，请选择**显示可以生成代码分析错误的规则**。  
  
-   若要显示和隐藏分配了警告操作规则之间切换，请选择**显示可以生成代码分析警告的规则**。  
  
-   若要切换显示和隐藏分配了规则**无**操作，选择**显示未启用的规则**。  
  
-   若要添加或移除的 Microsoft 默认规则集向当前的规则集，选择**添加或删除子规则集**。