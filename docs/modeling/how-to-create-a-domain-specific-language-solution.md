---
title: "如何： 创建域特定语言解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: "41"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：创建域特定语言解决方案
通过一个专用创建域特定语言 (DSL)[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]解决方案。  
  
## <a name="prerequisites"></a>先决条件  
 在可以开始此过程之前，你必须首先安装这些组件：  
  
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
  
    2.  此时将出现 “新建项目” 对话框。  
  
    3.  下**项目类型**，展开**其他项目类型**节点，然后单击**扩展性**。  
  
    4.  单击**域特定语言设计器**。  
  
    5.  在**名称**框中，键入解决方案的名称。 单击“确定”。  
  
         **域特定语言设计器向导**显示。  
  
        > [!NOTE]
        >  最好你键入的名称应是一个有效的 Visual C# 标识符，因为它可能用于生成代码。  
  
     ![创建 DSL 对话框](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  选择 DSL 模板。  
  
     上**选择域特定语言选项**页上，选择其中一个解决方案模板例如**最小语言**。 选择模板类似于你想要创建 DSL。  
  
     有关解决方案模板的详细信息，请参阅[选择的域特定语言解决方案模板](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
3.  在输入文件扩展名**文件扩展名**页。 它应是唯一的在你的计算机，并且你想要安装 DSL 中在其上的任何计算机。 你应看到消息**没有任何应用程序或 Visual Studio 编辑器使用此扩展**。  
  
    -   如果你在尚未完全安装的上一个实验 Dsl 中使用的文件扩展名，则可以清除它们出通过使用**重置实验实例**工具，可在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]SDK 菜单。  
  
    -   如果另一个[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用此文件扩展名扩展名的完全安装在计算机上，请考虑卸载它。 上**工具**菜单上，单击**扩展管理器**。  
  
4.  检查，并如有必要的调整，请在其余向导页中的字段。 当你对设置满意后时，单击**完成**。 有关设置的详细信息，请参阅[DSL 设计器向导页](#settings)。  
  
     向导将创建具有两个项目，分别名为的解决方案**Dsl**和**DslPackage**。  
  
    > [!NOTE]
    >  如果你看到一条消息，提醒你不从受信任的源运行文本模板，请单击**确定**。 你可以设置不会再次出现此消息。  
  
##  <a name="settings"></a>DSL 设计器的向导页  
 你可以将多个字段从其默认值保持不变。 但是，请确保设置的文件扩展名字段。  
  
### <a name="solution-settings-page"></a>解决方案设置页  
 **要根据你的域特定语言的哪个模板？**  
 选择模板类似于你想要创建 DSL。 不同的模板提供了方便的起始点。 当你选择的解决方案模板时，该向导将显示说明。 有关解决方案模板的详细信息，请参阅[选择的域特定语言解决方案模板](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 **你想要将你的域特定语言？**  
 默认值为解决方案名称。 此值生成代码。 它必须是有效作为 C# 类名称。  
  
### <a name="file-extension-page"></a>文件扩展页  
 **哪些扩展应模型文件使用？**  
 键入新的文件扩展名。  
  
 验证，此文件扩展名不已注册用于此计算机，如下所示：  
  
 查看下方显示**其他工具和应用程序注册用于处理此扩展**。 如果你看到消息**没有任何应用程序或 Visual Studio 编辑器使用此扩展**，则你可以使用此文件扩展名。  
  
 如果你看到工具或包的列表，你应执行以下任一操作：  
  
-   键入不同的文件扩展名。  
  
     \- 或 -  
  
-   重置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]实验实例。 这将注销所有你曾经构建 dsl 相关联。 上**启动**菜单上，单击**所有程序**， **Microsoft Visual Studio 2010 SDK**，**工具**，，然后**重置Microsoft Visual Studio 2010 实验实例**。 你可以重新生成你想要再次使用的任何其他 Dsl。  
  
     \- 或 -  
  
-   如果[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用此文件扩展名扩展名的完全安装在计算机上，卸载它。 上**工具**菜单上，单击**扩展管理器**。  
  
### <a name="product-settings-page"></a>产品设置页  
 **新的域特定语言所属产品的名称是什么？**  
 默认值为 DSL 名称。  
  
 在 Windows 资源管理器 （或文件资源管理器） 来描述具有此文件扩展名的文件使用此值。  
  
 **产品所属的公司的名称是什么？**  
 你的公司名称。  
  
 此值将合并到你 DSL 包的程序集信息属性。  
  
 **此解决方案中项目的根命名空间是什么？**  
 这将默认为由你公司的名称和产品名称。  
  
### <a name="signing-page"></a>签名页  
 **创建强名称密钥文件**  
 默认选择是创建新的密钥对你 DSL 的程序集进行签名。  
  
 **使用现有的强名称密钥**  
 如果你想要将 DSL 与另一个程序集相集成，请使用此选项。  
  
 有关强命名的详细信息，请参阅[创建和使用具有强名称程序集](http://go.microsoft.com/fwlink/?LinkId=186073)。  
  
## <a name="see-also"></a>另请参阅  
 [如何定义的域特定语言](../modeling/how-to-define-a-domain-specific-language.md)   
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
