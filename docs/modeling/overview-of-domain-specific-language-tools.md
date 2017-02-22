---
title: "域特定语言工具的概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
caps.handback.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 域特定语言工具的概述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

域特定语言工具 \(DSL 工具\)，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]承载，可以设计域特定语言 \(dsl\) 然后生成所有用户必须创建基于该语言的模型。  
  
 下列工具在 DSL 工具包括:  
  
-   使用不同的解决方案模板帮助的项目向导 " 在开始开发一个域特定语言。  
  
-   创建和编辑特定于域的语言定义一个图形设计器。  
  
-   确保以验证引擎域特定语言定义格式良好，则显示错误和警告，如果存在问题。  
  
-   采用一个域特定语言定义作为输入并导致源代码作为输出的代码生成器。  
  
## DSL 工具解决方案  
 域特定设计器向导提供以下解决方案模板:  
  
-   任务流  
  
-   类图  
  
-   最小的语言  
  
-   组件模型  
  
-   最小的 WPF  
  
-   最小 Windows.Forms  
  
-   DSL 库  
  
 有关更多信息，请参见 [选择域特定语言解决方案模板](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 向导创建具有以下项的一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案:  
  
-   DSL  
  
     DSL 项目定义域特定语言及其编辑的和进程的工具。  
  
-   **DslPackage**  
  
     DslPackage 项确定语言工具如何与集成 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## DSL 工具图形界面  
 可以使用 DSL 工具图形界面将元素和关系到域特定语言。  在添加元素之后，可以通过映射到形状，自定义颜色和添加修饰器定义其外观。  还可以将元素添加到工具箱中。  
  
## 在 DSL 工具的验证  
 DSL 提供验证的一个级别，以确保域模型与代码生成的基本要求。  通常，那么，当您创建时将拥有域特定语言，您将拥有验证表示业务逻辑规则。  有关自定义验证的更多信息，请参见 [域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)。  
  
 建议您通常以验证此修复域特定语言，在设计时。  如果该域特定语言出现验证错误，则无法生成源代码。  从模板生成的源代码处理通过单击 **转换所有模板** 执行在解决方案资源管理器工具栏。  每当修改语言定义，请确定对 **转换所有模板**。  有关更多信息，请参见 [如何：创建域特定语言解决方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
## DSL 工具的自定义项  
 可以提供其他的代码改进设计的行为和定义在该语言的约束。  如果需要，可以修改文本模板进行重大更改。  
  
## 分配 DSL 解决方案  
 DSL 工具生成在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]承载的包。  包显示工具箱、 DSL 资源管理器和使用这种域特定语言，它允许用户创建模型中的其他 UI 元素。  
  
 在生成并运行 DSL 工具在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的解决方案时， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 第二个实例显示可以为域特定语言如何查找对该语言的用户。 在确认一切正常工作后，可以将自己在 DslPackage 项目的生成文件夹中查找的 `.vsix` 文件。  此文件可用于安装 DSL 作为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展到其他计算机上。  有关更多信息，请参见 [部署域特定语言解决方案](../modeling/deploying-domain-specific-language-solutions.md)。  
  
## 请参阅  
 [实验实例](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)