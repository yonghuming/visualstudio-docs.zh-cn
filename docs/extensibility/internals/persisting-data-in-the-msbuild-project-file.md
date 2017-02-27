---
title: "MSBuild 项目文件中保存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目文件，保留中的数据"
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# MSBuild 项目文件中保存数据
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目子类型可能需要保留特定于子类型的数据到项目文件以供将来使用。  项目子类型使用项目文件持久性满足以下要求:  
  
1.  保存数据用作生成项目的一部分。  \(有关 Microsoft Build Engine 的更多信息，请参见 [MSBuild](http://msdn.microsoft.com/zh-cn/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)。\)与生成有关的信息可以:  
  
    1.  独立于配置数据。  即在 MSBuild 元素存储的数据的空白或缺少情况。  
  
    2.  配置相关数据。  即为特定项目配置时适合的 MSBuild 元素存储的数据。  例如：  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  保留不相关生成的数据。  不验证 XML 架构的数据可以使用任意形式的 XML 表示形式。  
  
    1.  独立于配置数据。  
  
    2.  配置相关数据。  
  
## 保持与生成有关的信息  
 数据持久性用于生成项目通过 MSBuild 进行处理。  MSBuild 系统维护与生成有关的信息一个主表。  项目子类型访问此数据安全负责并设置属性值。  项目子类型也可以扩展与生成有关的数据表通过将保持的其他属性和移除属性，使它们不会保留。  
  
 若要修改 MSBuild 数据，项子类型到检索 MSBuild 属性对象负责从基项目系统将 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 是在核心项目系统和复合项目的子类型查询实现的接口它的通过运行 `QueryInterface`。  
  
 下面的过程概述移除的属性步骤使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  
  
#### 从 MSBuild 项目文件中移除属性  
  
1.  对项目子类型的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 的 `QueryInterface` 。  
  
2.  调用带有 `pszPropName` 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> 设置为要移除的属性。  
  
### 保留的非编译相关信息  
 不重要生成数据的持久性在项目文件中通过 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>进行处理。  
  
 可以实现在主 `project subtype aggregator` 对象， `project subtype project configuration` 对象或二者的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 。  
  
 以下问题轮廓有关非编译相关信息持久性的主要概念。  
  
-   该基项目在主项目子类型 \(即最外面的项目子类型\) 聚合函数对象调用加载和保存配置独立数据，因此，它在项目子类型项目配置对象调用加载或保存依赖于配置数据。  
  
-   该基项目调用 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 多次方案项子类型总结的每个级别，并将每个级别的 GUID。  
  
-   该基项目传递或接收专用于特定项目子类型的 XML 片段并且使用此结构作为保持的状态方式在摘要级别之间的。  
  
-   该基项目调用传入 GUID 的最外面的项目子类型的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>实现。  如果 GUID 属于最外面的项目子类型，它处理调用，否则它将调用委托给内部项子类型，依此类推，，直到 GUID 对应于查找项的子类型。  
  
-   ，它将调用委托给内部项子类型之前，项目子类型还可以更改 XML 片段。  下面的示例演示一个抽象从项目文件，该文件的名称包含属性特定于项目子类型，向该项目子类型。  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## 请参阅  
 [项目子类型](../../extensibility/internals/project-subtypes.md)