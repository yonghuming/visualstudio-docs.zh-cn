---
title: "“规则集编辑器”对话框（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "“规则集编辑器”对话框"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# “规则集编辑器”对话框（旧版）
本主题介绍如何使用旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的**“规则集编辑器”**对话框。在需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 **“规则集编辑器”**对话框用于创建和修改 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)（可能为英文网页）规则集，这些规则集将序列化为 .rules 文件。  
  
> [!NOTE]
>  如果要用**“带编码的 XML 编辑器”**打开 .rules 文件，必须先关闭工作流或活动的关联设计器窗口。  
  
 有关如何访问**“规则集编辑器”**对话框的信息，请参见[如何：创建 PolicyActivity 规则集（旧版）](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)。  
  
> [!WARNING]
>  用于面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的规则编辑器不支持多目标。  
  
 下表描述了**“规则集编辑器”**对话框的用户界面 \(UI\) 元素。  
  
|UI 元素|说明|  
|-----------|--------|  
|**添加规则**|向规则集中添加一个新规则定义。|  
|**删除**|从规则集中删除选定的规则。|  
|**链接**|指定要将哪种类型的正向链接用于规则集。可用的选项包括：<br /><br /> -   **“完全链接”**，该选项指定使用所有正向链接机制：隐式机制、方法属性设置机制，以及使用 **Update** 函数的显式机制。<br />-   **“顺序”**，该选项指定不使用任何正向链接。<br />-   **“仅显式更新”**，该选项指定只对**“更新”**操作执行正向链接。<br /><br /> 有关正向链接的更多信息，请参见[使用 PolicyActivity 活动](http://go.microsoft.com/fwlink?LinkID=65004)（可能为英文网页）。|  
|**名称**|规则集列表的列标题。单击可按名称对规则列表排序。|  
|**优先级**|规则集列表的列标题。单击可按优先级对规则列表排序。|  
|**重新计算**|规则集列表的列标题。单击可按重新计算类型对规则列表排序。|  
|**规则预览**|规则集列表的列标题。单击可按规则的条件和操作预览对规则列表排序。|  
|**名称:**|输入规则的名称。|  
|**优先级:**|为规则输入一个优先级。默认优先级是 0。|  
|**重新计算:**|指定要将哪种规则重新计算类型用于规则。可用的选项包括：<br /><br /> -   **“始终”**，如果指定该选项，则会根据需要重新计算规则。<br />-   **“永不”**，如果指定该选项，将永远不会重新计算规则。在此情况下，规则只执行一次。|  
|**活动**|选中以激活规则。|  
|**条件:**|为规则条件输入一个表达式。有关表达式语法的信息，请参见本页的“输入条件和操作表达式”一节。|  
|**Then 操作:**|为 Then 操作输入表达式。有关表达式语法的信息，请参见本页的“输入条件和操作表达式”一节。|  
|**Else 操作:**|为 Else 操作输入表达式。有关表达式语法的信息，请参见本页的“输入条件和操作表达式”一节。|  
|**确定**|单击可将规则集保存为 .rules 文件。|  
  
 有关规则集的更多信息，请参见[使用 PolicyActivity 活动](http://go.microsoft.com/fwlink?LinkID=65004)（可能为英文网页）。  
  
## 输入条件和操作表达式  
 在**“规则集编辑器”**对话框的相应文本框中以文本方式为条件以及 Then 和 Else 操作输入表达式。您可以在编辑器中键入 **this.**，以使用 IntelliSense 类型的菜单引用工作流中使用的字段、属性和方法。或者，可以直接键入工作流成员名称。通过键入后跟方法名称的类名，您可以对引用的类型调用静态方法。  
  
 可以向条件中添加逻辑运算符（如 AND、OR 和 NOT）。也可以添加谓词。谓词由一个二进制运算符和两个操作数组成。支持的二进制运算符包括 \=\=、\>、\<、\>\= 和 \<\=。支持的操作数包括常量值、算术函数和作用域公共成员。  
  
 您可以指定比较的类型，也可以与 **null** 或空字符串进行比较。您可以嵌套包含复杂类型的变量成员调用，例如，`this.Address.State == "WA"`。  
  
 表达式支持下列运算符：  
  
-   关系运算符：\=\=、\=、\!\=  
  
-   比较运算符：\<、\<\=、\>、\>\=  
  
-   算术运算符：\+、\-、\*、\/、MOD  
  
-   逻辑运算符：AND、&&、OR、&#124;&#124;、NOT、\!  
  
-   位运算符：&、&#124;  
  
 表达式运算符优先级遵循 C\# 运算符优先级规则。  
  
 有关条件的更多信息，请参见[Using Conditions in Workflows](http://msdn.microsoft.com/zh-cn/541211f5-d382-4810-894f-71f00b34fa77)。  
  
### Halt 和 Update 函数  
 **“Then 操作:”**和**“Else 操作:”**表达式支持 **Halt** 和 **Update** 函数。若要使用 **Halt** 函数，请在**“Then 操作:”**或**“Else 操作:”**文本框中键入 **Halt**。**Halt** 操作会导致规则集执行立即停止，并且控制权将返回到调用代码。将 **Update** 函数与正向链接一起使用。  
  
 可以采用两种形式之一在编辑器中表示 **Update** 语句；下面的示例中演示了这两种形式：  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 有关将 **Update** 与正向链接一起使用的更多信息，请参见[使用 PolicyActivity 活动](http://go.microsoft.com/fwlink?LinkID=65004)（可能为英文网页）。  
  
## 请参阅  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [“选择规则集”对话框（旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [使用 PolicyActivity 活动](http://go.microsoft.com/fwlink?LinkID=65004)   
 [在工作流中使用条件](http://go.microsoft.com/fwlink?LinkID=65009)