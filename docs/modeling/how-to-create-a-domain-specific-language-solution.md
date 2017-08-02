---
title: "如何︰ 创建域特定语言解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：创建域特定语言解决方案
域特定语言 (DSL) 通过使用一个专用创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]解决方案。  
  
## <a name="prerequisites"></a>先决条件  
 在开始此过程之前，必须首先安装这些组件︰  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio 可视化和建模 SDK||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>创建域特定语言解决方案  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>若要创建域特定语言解决方案  
  
1.  启动 DSL 向导。  
  
    1.  在 **“文件”** 菜单上，指向 **“新建”**，然后单击 **“项目”**。  
  
    2.  此时将出现 **“新建项目”** 对话框。  
  
    3.  在下**项目类型**，展开**其他项目类型**节点，然后单击**扩展性**。  
  
    4.  单击**域特定语言设计器**。  
  
    5.  在**名称**框中，键入解决方案的名称。 单击“确定”。  
  
         **域特定语言设计器向导**出现。  
  
        > [!NOTE]
        >  最好你键入的名称应是有效的 Visual C# 标识符，因为它可能用于生成代码。  
  
     ![创建 DSL 对话框](~/modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  选择一个 DSL 模板。  
  
     在**选择域特定语言选项**页上，选择解决方案模板中的一个如**最小语言**。 选择的模板，则类似于你想要创建 DSL。  
  
     有关解决方案模板的详细信息，请参阅[选择域特定语言解决方案模板](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
3.  在输入文件扩展名的**文件扩展名**页。 它应该是唯一在您的计算机，并且想要安装 DSL 中在其上的任何计算机。 您应该看到消息**没有应用程序或 Visual Studio 编辑器使用此扩展插件**。  
  
    -   如果您曾经用以前尚未完全安装的实验性 Dsl 的文件扩展名，则可以清除它们出使用**重置实验实例**工具，可在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]SDK 菜单。  
  
    -   如果另一个[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用此文件扩展名扩展名的完全安装在计算机上，请考虑卸载它。 在**工具**菜单上，单击**扩展管理器**。  
  
4.  检查，并且如有必要调整，请在向导的剩余页面中的字段。 当对设置满意时，请单击**完成**。 有关设置的详细信息，请参阅[DSL 设计器向导页](#settings)。  
  
     向导将创建一个解决方案，有两个项目，分别名为**Dsl**和**DslPackage**。  
  
    > [!NOTE]
    >  如果您看到一条消息，不提示您要运行来自不受信任源的文本模板，请单击**确定**。 您可以设置不会再次出现此消息。  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>DSL 设计器向导页  
 您可以将多个字段从其默认值保持不变。 但是，请确保将文件扩展名字段设置。  
  
### <a name="solution-settings-page"></a>解决方案设置页  
 **要使基于您的域特定语言的模板？**  
 选择的模板，则类似于你想要创建 DSL。 不同的模板提供了方便的切入点。 当您选择的解决方案模板时，向导将显示说明。 有关解决方案模板的详细信息，请参阅[选择域特定语言解决方案模板](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 **你想要将命名为域特定语言？**  
 默认值为该解决方案的名称。 此值从生成代码。 它必须是作为 C# 类名无效。  
  
### <a name="file-extension-page"></a>文件扩展名页  
 **哪些扩展应模型文件使用？**  
 键入新的文件扩展名。  
  
 验证，此文件扩展名不已注册以便在此计算机中使用，如下所示︰  
  
 查看下方显示**其他工具和应用程序注册为处理此扩展插件**。 如果看到消息**没有应用程序或 Visual Studio 编辑器使用此扩展插件**，则可以使用此文件扩展名。  
  
 如果您看到工具或包的列表，您应执行以下任一操作︰  
  
-   键入不同的文件扩展名。  
  
     \- 或 -  
  
-   重置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]实验实例。 这将取消注册所有您以前生成的 Dsl。 在**启动**菜单上，单击**所有程序**， **Microsoft Visual Studio 2010 SDK**，**工具**，然后**重置 Microsoft Visual Studio 2010 实验实例**。 您可以重新生成你想要再次使用的任何其他 Dsl。  
  
     \- 或 -  
  
-   如果[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用此文件扩展名扩展名的完全安装在您的计算机上，将其卸载。 在**工具**菜单上，单击**扩展管理器**。  
  
### <a name="product-settings-page"></a>产品设置页  
 **新的域特定语言所属的产品名称是什么？**  
 默认值为 DSL 名称。  
  
 在 Windows 资源管理器 （或文件资源管理器） 来描述具有此文件扩展名的文件中使用此值。  
  
 **产品所属的公司名称是什么？**  
 你的公司名称。  
  
 此值将合并到 DSL 程序包的程序集信息属性。  
  
 **此解决方案中的项目的根命名空间是什么？**  
 这将默认为创建从您的公司的名称和产品名称。  
  
### <a name="signing-page"></a>签名页  
 **创建强名称密钥文件**  
 默认选项是创建新的密钥 DSL 程序集进行签名。  
  
 **使用现有的强名称密钥**  
 如果您想要将你的 DSL 与另一个程序集相集成，请使用此选项。  
  
 有关强命名的详细信息，请参阅[创建和使用具有强名称程序集](http://go.microsoft.com/fwlink/?LinkId=186073)。  
  
## <a name="see-also"></a>另请参阅  
 [如何定义特定于域的语言](../modeling/how-to-define-a-domain-specific-language.md)   
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

