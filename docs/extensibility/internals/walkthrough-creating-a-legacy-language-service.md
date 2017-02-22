---
title: "演练︰ 创建传统语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "创建语言服务 [托管的包框架]"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练︰ 创建传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用托管的包框架 \(MPF\) 语言类实现中的语言服务 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 非常简单。 您需要 VSPackage 来宿主语言服务，语言服务本身和用于您的语言的分析器。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../../extensibility/visual-studio-sdk.md)。  
  
## Visual Studio 包项目模板的位置  
 在中的三个不同的模板位置可以找到 Visual Studio 程序包项目模板 **新项目** 对话框中︰  
  
1.  在“Visual Basic 扩展性”之下。 项目的默认语言为 Visual Basic。  
  
2.  在“C\# 扩展性”之下。 项目的默认语言为 C\#。  
  
3.  在“其他项目类型扩展性”之下。 项目的默认语言为 C\+\+。  
  
### 创建的 VSPackage  
  
1.  使用 Visual Studio Package 项目模板创建新的 VSPackage。  
  
     如果要添加到现有的 VSPackage 的语言服务，跳过以下步骤，直接转到"创建语言服务类"过程。  
  
2.  MyLanguagePackage 输入项目的名称，再单击 **确定**。  
  
     可以使用所需的任意名称。 此处详细介绍这些过程假定 MyLanguagePackage 作为名称。  
  
3.  选择 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 语言以及用于生成新的密钥文件的选项。 单击**“下一步”**。  
  
4.  输入相应的公司和包信息。 单击**“下一步”**。  
  
5.  选择 **菜单命令**。 单击**“下一步”**。  
  
     如果不想支持代码段，您可以只需单击完成并忽略下一步。  
  
6.  输入 **插入代码段** 作为 **命令名称** 和 `cmdidInsertSnippet` 为 **命令 ID**。 单击**“完成”**。  
  
     **命令名称** 和 **命令 ID** 可以是任何所需，它们只是示例。  
  
### 创建语言服务类  
  
1.  在 **解决方案资源管理器**, ，右键单击该 MyLanguagePackage 项目，选择 **添加**, ，**引用**, ，然后选择 **添加新引用** 按钮。  
  
2.  在 **添加引用** 对话框中，选择 **Microsoft.VisualStudio.Package.LanguageService** 中 **.NET** 选项卡上，单击 **确定**。  
  
     这需要进行一次只能为语言包项目。  
  
3.  在 **解决方案资源管理器**, ，右击 VSPackage 项目，选择 **添加**, ，**类**。  
  
4.  请确保 **类** 在模板列表中选择。  
  
5.  输入 **MyLanguageService.cs** 名称的类文件，并单击 **添加**。  
  
     可以使用所需的任意名称。 此处详细介绍这些过程假设 `MyLanguageService` 作为名称。  
  
6.  在 MyLanguageService.cs 文件中，添加以下 `using` 语句。  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  修改 `MyLanguageService` 类派生自 <xref:Microsoft.VisualStudio.Package.LanguageService> 类︰  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  将光标放在"LanguageService"，从 **编辑**, ，**IntelliSense** 菜单上，选择 **实现抽象类**。 这将添加最小必需的方法来实现的语言服务类。  
  
9. 实现抽象方法，如中所述 [实现语言服务](../../extensibility/internals/implementing-a-legacy-language-service2.md)。  
  
### 注册语言服务  
  
1.  打开 MyLanguagePackagePackage.cs 文件并添加以下 `using` 语句︰  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  注册您的语言服务类，如中所述 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)。 这包括 ProvideXX 属性和"Proffering 语言服务"部分。 使用本主题中使用 TestLanguageService MyLanguageService。  
  
### 分析器和扫描程序  
  
1.  实现分析器和扫描您的语言程序中所述 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
     如何实现您的分析器和扫描程序完全取决于您并不属于本主题的讨论范围。  
  
## 语言服务功能  
 若要实现语言服务中的每项功能，您通常适当 MPF 语言服务类中派生一个类、 必要时，实现所有抽象方法和重写适当的方法。 你想要支持创建和\/或派生自哪些类是依赖的功能。 中详细地讨论这些功能 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)。 下面的过程是从 MPF 类派生一个类为常规方法。  
  
#### 派生自 MPF 类  
  
1.  在 **解决方案资源管理器**, ，右击 VSPackage 项目，选择 **添加**, ，**类**。  
  
2.  请确保 **类** 在模板列表中选择。  
  
     输入一个合适的名称的类文件，然后单击 **添加**。  
  
3.  在新的类文件中，添加以下 `using` 语句。  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  修改要从所需的 MPF 类派生的类。  
  
5.  添加至少采用相同参数作为基类的构造函数的类构造函数并传递到基类构造函数的构造函数参数。  
  
     例如，一个类的构造函数派生自 <xref:Microsoft.VisualStudio.Package.Source> 类可能如下所示︰  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  从 **编辑**, ，**IntelliSense** 菜单上，选择 **实现抽象类** 类的基类是否必须实现所有抽象方法。  
  
7.  否则为放置在类中插入符号，并输入要被重写的方法。  
  
     例如，键入 `public override` 以查看所有可以在此类中重写的方法的列表。  
  
## 请参阅  
 [实现传统语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)