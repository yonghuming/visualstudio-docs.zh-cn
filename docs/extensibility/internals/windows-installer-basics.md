---
title: "Windows 安装程序基础知识 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Installer Vspackage"
  - "Vspackage，Windows 安装程序基础知识"
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Windows 安装程序基础知识
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Windows 安装程序安装和卸载应用程序或用户的计算机上的软件产品名 （有时称为 WICs 或只是组件） 的 Windows 安装程序组件的单元中执行这些任务。 一个 GUID 标识每个 WIC，这是安装和引用计数对于使用 Windows Installer 安装的基本单位。  
  
 Windows 安装程序的综合文档，请参阅 Platform SDK 主题 [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)。  
  
## 创作 VSPackage  
 Windows 安装程序使用安装包，其中包含 Windows 安装程序需要安装、 卸载或修复产品并运行安装程序用户界面 \(UI\) 的信息。 每个安装包包括一个.msi 文件，其中包含安装数据库、 摘要的信息流，以及安装的各个部分的数据流。 若要使用安装程序，您必须创作安装。 安装程序将组织的概念组件的安装，并将有关安装的信息存储在关系数据库，因为广泛创作一个安装包的过程需要执行以下步骤︰  
  
1.  规划您编写，以支持您的版本控制和通过并行策略的安装程序。  
  
2.  确定要呈现给用户的功能。  
  
3.  将 VSPackage 和依赖项组织到组件。  
  
4.  安装使用填充数据库的信息。  
  
5.  验证安装包。  
  
 本文档主要关心过程的第一个和第三个步骤。 在这些步骤中您将组织 VSPackage 功能到 WICs 以便可以框架版本控制和服务策略才能实现的后续版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其余三个步骤所详述的平台 SDK 中的 Windows Installer 文档中。  
  
## 关键术语  
 以下是与 Windows Installer 技术相关的关键术语的定义。  
  
 资源  
 文件、 注册表项、 快捷方式，或，依此类推，后者可能会安装到一台计算机。 这些资源进行逻辑分组到 Windows 安装程序组件中。  
  
 Windows 安装程序组件 \(WIC\)  
 表示已安装并卸载作为一个单元的相关资源的逻辑分组的安装基本单位。 Windows Installer 组件由独特的组件 ID 或 GUID 标识。 此外，Windows Installer 保留其引用计数在 WIC 级别。 实现最大版本控制的灵活性，将不能超过一个主要资源，例如一个 DLL，纳入给定 WIC。 请注意，标识和填充 WIC，使其使用的 GUID，并将其部署后，您不能更改其构成。 有关详细信息，请参阅 [组织应用程序分解为组件](http://msdn.microsoft.com/library/aa370561.aspx)。  
  
 包 （Redist 包）  
 此文件可能会指向某一.msi 文件和外部源的文件组成的部署单元。 包包含 Windows 安装程序需要运行用户界面以安装或卸载该应用程序的所有信息。  
  
 .msi 文件  
 包含说明和安装应用程序所需数据的 COM 结构化存储文件。 每个包包含至少一个.msi 文件。 .Msi 文件包含安装程序数据库、 摘要的信息流，并可能是一个或多个转换和内部的源代码文件。 要安装的文件可以压缩为 cab 文件和存储在.msi 文件中的流或存储、 压缩，或未压缩的.msi 文件的源媒体上外部。 有关详细信息，请参阅 [Windows 安装程序文件扩展名](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx)。  
  
## Windows 安装程序规则强制  
 两组规则确定部署到安装程序的组件的资源。 虽然应实施作为安装的创作者的第二个集由 Windows 安装程序本身，维护一个规则集。  
  
> [!NOTE]
>  仅当您运行.msi 文件的验证，会发生的 Windows 安装程序规则的实施。 不过，警告将这些规则视为最佳做法。 有关详细信息，请参阅 [验证安装数据库](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) 和 [包验证](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx)。  
  
#### 安装程序强制实施的规则  
  
-   给定组件中的所有文件必须都安装到同一个目录。 相反，安装到不同的文件夹的文件必须属于单独的组件。  
  
-   可能有每个组件，只有一个注册表项路径。 注册表项路径是只是该文件或注册表项，表示整个部分。  
  
#### 组件服务提供商的责任  
  
-   在后续版本中可能会分别提供任何两个资源应存在于单独的组件。 仅当您确信永远不会将分别发布这些资源时，应将资源分组到同一组件。 事实上，建议所有主要资源 \(例如 Dll\) 始终存在于单独 WICs。 有关详细信息，请参阅 [定义安装程序组件](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx)。  
  
-   无版本控制的资源不断应在多个 WIC 装运。  
  
## 请参阅  
 [如果组件规则均未损坏，会发生什么情况？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)