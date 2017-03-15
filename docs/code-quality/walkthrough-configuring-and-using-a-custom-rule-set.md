---
title: "演练：配置和使用自定义规则集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析, 演练"
  - "代码分析, 规则集"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# 演练：配置和使用自定义规则集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练演示如何使用已配置为对类库使用自定义规则集的代码分析工具。  您可以选择与为解决方案指定的项目类型相关的规则集，也可以选择备用规则集来满足特定需求（例如，扫描旧版代码以查找可用非中断方式修复的问题）。  在上述任何一种情况下，都还可以自定义规则集以按照项目要求对其进行微调。  
  
 在本演练中，您将逐步完成以下过程：  
  
-   创建类库。  
  
-   选择**“Microsoft 基本设计准则规则”**代码分析规则集。  
  
-   将自己的代码添加到类中。  
  
-   运行代码分析。  
  
-   自定义规则集。  
  
-   运行代码分析并查看规则集自定义行为的工作方式。  
  
## 系统必备  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## 对代码分析使用规则集  
 首先，创建一个简单的类库。  
  
#### 创建类库  
  
1.  在**“文件”**菜单上，单击**“新建”**，然后单击**“项目”**。  
  
2.  在“新建项目”对话框中，单击“项目类型”下的“Visual C\#”。  
  
3.  在**“Visual C\#”**下，选择**“类库”**。  
  
4.  在**“名称”**文本框中，键入“RuleSetSample”，然后单击**“确定”**。  
  
 接着，您将选择**“Microsoft 基本设计准则规则”**规则集并将其随项目一起保存。  
  
#### 选择代码分析规则集  
  
1.  在**“分析”**菜单上，单击**“为 RuleSetSample 配置代码分析”**。  
  
     将显示代码分析的配置设置。  
  
2.  在**“运行此规则集”**下拉列表中，选择**“Microsoft 的所有规则”**。  
  
     有关可用规则集的更多信息，请参见[代码分析规则集参考](../code-quality/code-analysis-rule-set-reference.md)。  
  
     在“文件”菜单上单击**“保存选定项”**，以便用有关您所选规则集及其设置的信息更新项目文件。  
  
    > [!TIP]
    >  在实际情况中，为了优先处理您希望利用代码分析来发现的问题，最好开始时使用**“最少量建议规则”**规则集并更正所需的问题，然后逐渐添加更多规则或规则集以查找并更正其他问题。  
  
 接下来，您将向类库中添加一些代码，这些代码用于演示与 CA1704“标识符应正确拼写”代码分析规则的冲突。  有关详细信息，请参阅[CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
#### 添加自己的代码  
  
-   在解决方案资源管理器中，打开 Class1.cs 文件，然后将现有代码替换为以下代码：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }  
  
    ```  
  
 现在，您即可对 RuleSetSample 项目运行代码分析，然后在“错误列表”窗口中查找生成的所有错误和警告。  
  
#### 对 RuleSetSample 项目运行代码分析  
  
1.  在**“分析”**菜单上，单击**“对 RuleSetSample 运行代码分析”**。  
  
2.  在“错误列表”窗口中，单击**“警告”**，再单击**“说明”**列标题可以按字母数字顺序对警告进行排序。  
  
     在实际应用中，您可以在此时修复任何值得修复的规则冲突，如果您确定某个规则不值得修复，则可以选择关闭它或禁止显示它。  有关详细信息，请参阅[使用 SuppressMessage 特性禁止显示警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。  
  
3.  请注意 CA1704 警告。  与这条规则的这些冲突表明您应“考虑为参数提供更有意义的名称”。您可以按照下个步骤中的说明在代码中更正此问题或禁用该规则。  
  
 接着，您将自定义规则集以排除 CA1704 警告“标识符应正确拼写”。  
  
#### 针对项目自定义规则集以禁用特定规则  
  
1.  在**“分析”**菜单上，单击**“为 RuleSetSample 配置代码分析”**。  
  
2.  在**“运行此规则集”**下拉列表中，确认**“Microsoft 的所有规则”**规则集仍处于突出显示状态，然后单击**“打开”**。  此时将显示规则集页。  
  
3.  展开 Microsoft.Naming 类别节点，然后选择 CA1704 警告。  
  
4.  在**“操作”**列下，选择**“无”**。这可以防止 CA1704 在“错误列表”窗口中显示为警告或错误。  
  
     此时是您尝试使用各种工具栏按钮和筛选选项以熟悉它们的好时机。  例如，可以使用**“分组依据”**下拉列表来帮助查找特定的规则或规则类别。  再如，可以使用规则集页工具栏中的**“隐藏禁用的规则”**按钮来隐藏或显示**“操作”**列设置为**“无”**的所有规则。  如果需要扫描所有已关闭的规则以确认您仍然希望禁用这些规则，则这种方法很有用。  
  
5.  在“视图”菜单上，单击“属性窗口”。  在“属性”工具窗口的“名称”框中，键入 **My Custom Rule Set**。  执行此操作会更改新规则集在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE 中的显示名称。  
  
6.  在**“文件”**菜单上，单击**“保存 Microsoft All Rules.ruleset”**以保存自定义的规则集。  导航至项目的根文件夹。  在**“文件名”**文本框中，键入“MyCustomRuleSet”。  现在即可选择该自定义规则集，将它用于您的项目。  
  
 创建新规则集后，您必须配置项目设置以指定希望对项目使用该新规则集。  
  
#### 指定要对项目使用的新规则集  
  
1.  在解决方案资源管理器中，右击项目，然后选择**“属性”**。  
  
2.  在**“属性”**选项卡中，单击**“代码分析”**。  
  
     在“运行此规则集”下拉列表中，单击**\<浏览..\>**.  导航至代码项目的根文件夹，然后选择 MyCustomRuleSet.ruleset。  这是在上一个步骤中创建的新规则集。  
  
3.  在**“文件”**菜单上，单击**“保存”**以保存项目配置。  现在即可对项目使用该自定义规则集。  
  
 最后，您将使用 MyCustomRuleSet 规则集再次运行代码分析。  请注意，“错误列表”窗口不会显示与 CA1704 性能规则的冲突。  
  
#### 再次对 RuleSetSample 项目运行代码分析  
  
1.  在**“分析”**菜单上，单击**“对 RuleSetSample 运行代码分析”**。  
  
2.  请注意，当您在“错误列表”窗口中单击**“警告”**时，将不会再看到表示与“标识符应正确拼写”规则冲突的 CA1704 警告。  
  
## 请参阅  
 [如何：配置托管代码项目的代码分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [代码分析规则集参考](../code-quality/code-analysis-rule-set-reference.md)