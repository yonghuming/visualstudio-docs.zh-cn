---
title: "N 层数据应用程序概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 3949d49f763c2513e86c2cd3f1b20c20fb858ecc
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="n-tier-data-applications-overview"></a>N 层数据应用程序概述
*N 层*数据应用程序是数据应用程序分离到多个*层*。 N 层应用程序也称为"分布式应用程序"和"多层应用程序"，它们将处理分为分布式客户端和服务器之间的相互独立的层。 当开发数据访问应用程序时，你应具有组成应用程序各层之间形成清晰的隔离。  
  
典型的 n 层应用程序包括表示层、 一个中间层和数据层。 单独的 n 层应用程序中的各个层的最简单方法是创建每个层都想要包括在你的应用程序中的离散项目。 例如，表示层可能是 Windows 窗体应用程序，而数据访问逻辑可能是一个类库，位于中间层。 此外，表示层可能与通过服务之类的服务与中间层中的数据访问逻辑通信。 将应用程序组件分离到不同的层可提高应用程序的可维护性和可伸缩性。 有利于采用新技术，可以应用于单个层而无需重新设计整个解决方案执行此操作。 此外，n 层应用程序通常将敏感信息存储在中间层中，以便与表示层隔离。  
  
Visual Studio 包含几个功能，可帮助开发人员创建 n 层应用程序：  
  
-   数据集提供**数据集项目**属性，可用于将数据集 （数据实体层） 和 tableadapter 分离 （数据访问层） 到相互独立的项目。  
  
-   [LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供单独的命名空间中生成的 DataContext 和数据类的设置。 这样数据访问层和数据实体层的逻辑的分隔。  
  
-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)提供<xref:System.Data.Linq.Table%601.Attach%2A>使您能够将从应用程序中的不同层的 DataContext 组合在一起的方法。 有关详细信息，请参阅[N 层和远程应用程序而 LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)。  
  
## <a name="presentation-tier"></a>表示层  
*表示层*是指用户与应用程序进行交互时所在的层。 它通常还包含其他应用程序逻辑。 典型的表示层组件包括：  
  
-   数据绑定组件，如<xref:System.Windows.Forms.BindingSource>和<xref:System.Windows.Forms.BindingNavigator>。  
  
-   对象表示的数据，例如[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)在表示层中使用的实体类。  
  
表示层通常通过使用服务引用来访问中间层 (例如， [Windows Communication Foundation 服务和 Visual Studio 中的 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)应用程序)。 表示层不会直接访问数据层。 表示层与数据层通过中间层中的数据访问组件进行通信。  
  
## <a name="middle-tier"></a>中间层  
*中间层*表示层和数据层的层用于相互通信。 典型的中间层组件包括：  
  
-   业务逻辑，如业务规则和数据验证。  
  
-   数据访问组件和逻辑，如下所示：  
  
    -   [Tableadapter](create-and-configure-tableadapters.md)和[Dataadapter 和 Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。  
  
    -   对象表示的数据，例如[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)实体类。  
  
    -   常见的应用程序服务，例如身份验证、 授权和个性化设置。  
  
下图显示功能和技术在 Visual Studio 中可用并其中它们可能适合于 n 层应用程序的中间层。  
  
![中间层组件](../data-tools/media/ntiermid.png "NtierMid")  
中间层  
  
中间层通常可以通过使用数据连接连接到数据层。 此数据连接通常存储在数据访问组件中。  
  
## <a name="data-tier"></a>数据层  
*数据层*基本上是存储应用程序数据的服务器 (例如，运行的服务器[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)])。  
  
下图显示功能和技术在 Visual Studio 中可用并其中它们可能适合于 n 层应用程序的数据层。  
  
![数据层组件](../data-tools/media/ntierdatatier.png "ntierdatatier")  
数据层  
  
数据层不能直接从表示层中的客户端访问。 相反，在中间层的数据访问组件用于演示文稿和数据层之间的通信。  
  
## <a name="help-for-n-tier-development"></a>关于 N 层开发的帮助  
以下主题提供有关使用 n 层应用程序的信息：  
  
[将数据集和 TableAdapter 分离到不同的项目中](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
[演练：创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  

[N 层和远程应用程序而 LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>请参阅
[演练： 创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[分层更新](../data-tools/hierarchical-update.md)   
[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)   
[在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)