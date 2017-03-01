---
title: "如何︰ 修改标准的菜单命令在域特定语言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 10
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 571b30e0be9863b20dc1c8abca87940bb21cc344
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>如何：使用域特定语言修改标准的菜单命令
可修改某些在 DSL 中自动定义的标准命令的行为。 例如，您可以修改**剪切**，以便排除敏感信息。 若要实现此目的，请重写命令集类中的方法。 这些类定义在 CommandSet.cs 文件中，在 DslPackage 项目中，并从<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>。</xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>派生  
  
 总之，若要修改命令，请执行以下操作：  
  
1.  [发现可以修改的命令](#what)。  
  
2.  [创建相应命令集类的分部声明](#extend)。  
  
3.  [重写 ProcessOnStatus 和 ProcessOnMenu 方法](#override)命令。  
  
 本主题解释了此过程。  
  
> [!NOTE]
>  如果你想要创建您自己的菜单命令，请参阅[如何︰ 向快捷菜单添加命令](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。  
  
##  <a name="a-namewhata-what-commands-can-you-modify"></a><a name="what"></a>您可以修改哪些命令？  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>发现可以修改的命令  
  
1.  在`DslPackage`项目中，打开`GeneratedCode\CommandSet.cs`。 此 C# 文件可在解决方案资源管理器作为`CommandSet.tt`。  
  
2.  查找该文件中类的名称结尾"`CommandSet`"，例如`Language1CommandSet`和`Language1ClipboardCommandSet`。  
  
3.  在每个命令集类中，键入“`override`”，后跟一个空格。 IntelliSense 将显示可重写方法的列表。 每个命令具有一对其名称以“`ProcessOnStatus`”和“`ProcessOnMenu`”开头的方法。  
  
4.  记录哪些命令集类包含你想要修改的命令。  
  
5.  关闭该文件，无需保存编辑。  
  
    > [!NOTE]
    >  通常，不应编辑已生成的文件。 任何编辑都将在下次生成文件时丢失。  
  
##  <a name="a-nameextenda-extend-the-appropriate-command-set-class"></a><a name="extend"></a>扩展相应命令集类  
 创建包含命令集类的分部声明的新文件。  
  
#### <a name="to-extend-the-command-set-class"></a>扩展命令集类  
  
1.  在“解决方案资源管理器”中，在 DslPackage 项目中打开 GeneratedCode 文件夹，然后在 CommandSet.tt 下进行查找并打开其生成的文件 CommandSet.cs。 注意在此处定义的第一个类的命名空间和名称。 例如，你可能看到：  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  在**DslPackage**，创建一个名为**自定义代码**。 在此文件夹中，创建名为的新类文件`CommandSet.cs`。  
  
3.  在该新文件中，编写具有与生成的分部类相同的命名空间和名称的分部声明。 例如：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **请注意**如果类文件模板用于创建新的文件，则必须更正命名空间和类名。  
  
##  <a name="a-nameoverridea-override-the-command-methods"></a><a name="override"></a>重写命令方法  
 大多数命令都具有两个关联的方法︰ 方法提供名称喜欢`ProcessOnStatus`...来确定命令是否应该是可见且已启用。 它将在每当用户右键单击关系图时调用，并应快速执行且不做任何更改。 `ProcessOnMenu`...当用户单击该命令，并应执行该命令的函数时调用。 你可能想要重写其中一个方法，或两者都进行重写。  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>更改命令何时显示在菜单上  
 重写 ProcessOnStatus...方法。 此方法应设置其参数 MenuCommand 的“可见”和“已启用”属性。 通常，命令查看 this.CurrentSelection 来确定命令是否应用到选定的元素，还可能查看其属性来确定命令是否可以应用到其当前状态中。  
  
 一般原则是，“可见”属性应由选定了哪些什么元素来确定。 “已启用”属性（确定命令在菜单上是显示为黑色还是灰色）应取决于选择的当前状态。  
  
 以下示例将在用户已选择多个形状时禁用“删除”菜单项。  
  
> [!NOTE]
>  此方法不影响命令通过击键是否可用。 例如，禁用“删除”菜单项不会阻止通过 Delete 键来调用命令。  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 最佳做法是先调用基方法，以处理所有你无需考虑的用例和设置。  
  
 ProcessOnStatus 方法不应在“存储”中创建、删除或更新元素。  
  
### <a name="to-change-the-behavior-of-the-command"></a>更改命令的行为  
 重写 ProcessOnMenu...方法。 以下示例将阻止用户一次删除多个元素，即使使用 Delete 键也是如此。  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 如果你的代码将对“存储”进行更改（例如创建、删除或更新元素或链接），则必须在事务内进行这些更改。 有关详细信息，请参阅[如何创建和更新模型元素](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。  
  
### <a name="writing-the-code-of-the-methods"></a>编写方法的代码  
 以下片段通常在这些方法内十分有用：  
  
-   `this.CurrentSelection`。 用户右键单击的形状始终包含在此形状和连接符列表中。 如果用户单击关系图的空白部分，则“关系图”是该列表中的唯一成员。  
  
-   `this.IsDiagramSelected()` - `true`如果用户单击该关系图的空白部分。  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()` - 用户未选择多个形状  
  
-   `this.SingleSelection` - 用户右键单击的形状或关系图  
  
-   `shape.ModelElement as MyLanguageElement` - 由形状表示的模型元素。  
  
 有关如何进行导航元素元素以及有关如何创建对象和链接的详细信息，请参阅[导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ComponentModel.Design.MenuCommand></xref:System.ComponentModel.Design.MenuCommand>   
 [编写代码以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [如何︰ 向快捷菜单添加命令](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../extensibility/vsct-xml-schema-reference.md)   
 [VMSDK – 电路图示例。广泛的 DSL 自定义项](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [示例代码︰ 电路图](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

