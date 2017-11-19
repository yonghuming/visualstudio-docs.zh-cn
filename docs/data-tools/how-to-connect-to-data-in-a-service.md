---
title: "如何： 连接到服务中的数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 334f31dcd68e031bfb25b4e0dcd6ce55b9d2f20c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何：连接到服务中的数据
通过运行从服务返回的数据将应用程序连接[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)并选择**服务**上**选择数据源类型**页。  
  
 在向导完成，服务引用添加到你的项目，并可立即在[数据源窗口](add-new-data-sources.md)。  
  
> [!NOTE]
>  在显示的项**数据源**窗口都依赖于该服务返回的信息。 某些服务可能没有提供足够的信息供**数据源配置向导**创建可绑定的对象。 例如，如果该服务返回一个非类型化数据集，则显示任何项中**数据源窗口**完成该向导时。 这是因为非类型化数据集不提供架构，所以该向导没有足够的信息来创建数据源。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>若要连接到服务应用程序  
  
1.  在 **“数据”** 菜单上，单击 **“添加新数据源”**。  
  
2.  选择**服务**上**选择数据源类型**页，，然后单击**下一步**。  
  
3.  输入你想要使用，或单击该服务的地址**发现**在当前解决方案中，查找服务，然后单击**转**。  
  
4.  （可选） 一个新**Namespace**可以键入来替代默认值。  
  
    > [!NOTE]
    >  单击**高级**以打开[配置的服务引用对话框](../data-tools/configure-service-reference-dialog-box.md)。  
  
5.  单击**确定**添加到你的项目的服务引用。  
  
6.  单击 **“完成”**。  
  
     数据源添加到**数据源**窗口。  
  
## <a name="next-steps"></a>后续步骤  
  
#### <a name="to-add-functionality-to-your-application"></a>将功能添加到你的应用程序  
  
-   选择中的项**数据源**窗口并将其拖到窗体上创建绑定的控件。 有关详细信息，请参阅[将控件绑定到 Visual Studio 中的数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Visual Studio 中的 Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)