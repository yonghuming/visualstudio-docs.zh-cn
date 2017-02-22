---
title: "在单元测试中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成员 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# 在单元测试中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成员
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

单元测试框架支持在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中进行单元测试。  对单元测试进行编码时，请使用 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework> 命名空间中的类和成员。  当您从头开始编写了单元测试或要改进由测试的代码生成的单元测试时，您便可以使用这些类和成员。  
  
## 元素组  
 为了帮助提供对单元测试框架的更为清晰的概述，本节将 UnitTesting 命名空间的元素分为相关的功能组。  
  
> [!NOTE]
>  使用特性元素（其名称以字符串 Attribute 结尾）时，它可以带字符串 Attribute，也可以不带。  例如，下面的两个代码示例功能完全相同：  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### 用于数据驱动测试的元素  
 使用以下元素来设置数据驱动的单元测试。  有关更多信息，请参见[如何：创建数据驱动的单元测试](../test/how-to-create-a-data-driven-unit-test.md)和[演练：使用配置文件定义数据源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## 用于建立调用顺序的特性  
 用下列特性之一进行修饰的代码元素将在您所指定的时刻被调用。  有关更多信息，请参见[单元测试分析](http://msdn.microsoft.com/zh-cn/a03d1ee7-9999-4e7c-85df-7d9073976144)。  
  
### 对于程序集  
 在加载程序集之后以及卸载程序集之前，将调用 AssemblyInitialize 和 AssemblyCleanup。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### 对于类  
 在加载类之后以及卸载类之前，将调用 ClassInitialize 和 ClassCleanup。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### 对于测试方法  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## 用于标识测试类和方法的特性  
 每个测试类都必须具有 TestClass 特性，每个测试方法都必须具有 TestMethod 特性。  有关更多信息，请参见[单元测试分析](http://msdn.microsoft.com/zh-cn/a03d1ee7-9999-4e7c-85df-7d9073976144)。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Assert 类和相关异常  
 单元测试可以通过使用各种 Assert 语句、异常和特性来验证特定应用程序的行为。  有关更多信息，请参见[使用 Assert 类](../test/using-the-assert-classes.md)。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## TestContext 类  
 下列特性以及为其所赋的值显示在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中特定测试方法的“属性”窗口中。  这些特性并未设计为通过单元测试代码来访问。  相反，它们会通过 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 IDE 或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 测试引擎来影响使用或运行单元测试的方式。例如，其中的一些特性会在测试管理器窗口和测试结果窗口中显示为列，这表示您可以使用这些特性对测试和测试结果进行分组和排序。  此类特性之一是 TestPropertyAttribute，使用它可以向单元测试中添加任意元数据。  例如，可以使用它来存储此测试所涵盖的测试通过的名称，方法是使用 `[TestProperty("TestPass", "Accessibility")]` 对单元测试进行标记。  或者，您可以使用它来存储此类测试的指示符：\(`[TestProperty("TestKind", "Localization")]`\)。  您使用此特性创建的属性以及所赋的属性值都将显示在标题为**“测试特定的”**的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]“属性”窗口中。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## 测试配置类  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## 用于生成报告的特性  
 本节中的特性将它们所修饰的测试方法与 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 团队项目的项目层次结构中的实体相关联。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## 用于专用访问器的类  
 如[Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/zh-cn/2056c6a7-6672-42a7-8f53-fead33c56deb)中所述，您可以为私有方法生成单元测试。  此生成会创建专用访问器类，该类将实例化 PrivateObject 类的对象。  PrivateObject 类是一个包装类，它使用反射作为专用访问器进程的一部分。  PrivateType 类与之相似，但它用于调用私有静态方法，而不是调用私有实例方法。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>