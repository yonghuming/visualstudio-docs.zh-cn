---
title: "MSBuild 项目文件中的持久保存数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d41a4776362f450d5d55552b049c3bba1bc781b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild 项目文件中的持久保存数据
项目子类型可能需要将特定于子类型的数据保存到项目文件以供将来使用。 项目子类型使用项目文件持久性满足以下要求：  
  
1.  保留用作生成项目的一部分的数据。 (Microsoft 生成引擎的详细信息，请参阅[MSBuild](../../msbuild/msbuild.md)。)可以与生成相关的信息：  
  
    1.  独立于配置的数据。 即在与空或缺失的条件的 MSBuild 元素中存储的数据。  
  
    2.  依赖于配置的数据。 也就是说，以针对特定项目配置的 MSBuild 元素中存储的数据。 例如:   
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  保留无关生成的数据。 此数据可以表示自由格式的 xml 中不根据 XML 架构验证。  
  
    1.  独立于配置的数据。  
  
    2.  依赖于配置的数据。  
  
## <a name="persisting-build-related-information"></a>保存与生成相关的信息  
 通过 MSBuild 处理持久性数据可用于生成项目。 MSBuild 系统维护与生成相关信息的主表。 项目子类型负责访问此数据来获取和设置属性值。 通过添加要保留的其他属性，并删除属性，因此它们不会保留，项目子类型还可以增加与生成相关的数据表。  
  
 若要修改的 MSBuild 数据，项目子类型是负责从通过在基本项目系统中检索 MSBuild 属性对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>是一个接口，核心项目系统和聚合项目子类型查询上实现它，通过运行`QueryInterface`。  
  
 以下过程概述了用于删除属性使用的步骤<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>若要从 MSBuild 项目文件中删除属性  
  
1.  调用`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>项目子类型。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>与`pszPropName`设置为你想要删除的属性。  
  
### <a name="persisting-non-build-related-information"></a>保持非生成相关的信息  
 通过处理的项目文件中并不重要生成的数据持久性<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>。  
  
 你可以实现<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>上主要`project subtype aggregator`对象，`project subtype project configuration`对象，或两者。  
  
 以下几点介绍有关非生成相关信息的持久性的主要概念。  
  
-   基本项目对主项目子类型 （即的外面项目子类型） 聚合器对象调用用于加载和保存配置数据相互独立，并且它在加载或保存取决于配置项目子类型项目配置对象上调用数据。  
  
-   基本项目调用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>多个时间为每个项目子类型聚合级别，并传递每个级别的 GUID。  
  
-   基项目通过或接收 XML 片段，专用于特定项目子类型，并使用此机制作为一种聚合级别之间保持状态。  
  
-   基本项目调用的最外层项目子类型的<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>传递中 GUID 的实现。 如果 GUID 所属的最外层项目子类型，它将处理的调用，然后重试。否则它将调用委托给内部项目子类型，依此类推，直到找到 GUID 对应的项目子类型。  
  
-   项目子类型还可以修改 XML 片段之前或之后它将调用委托给内部项目子类型。 下面的示例演示了中的项目文件，其中包含特定于项目子类型，属性的文件的名称传递到该项目子类型的摘要。  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [项目子类型](../../extensibility/internals/project-subtypes.md)