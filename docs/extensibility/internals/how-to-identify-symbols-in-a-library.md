---
title: "如何： 标识库中的符号 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e7f810ff5ad1654081cd061edbc4360eb988402
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>如何： 标识库中的符号
符号浏览工具显示符号的分层的视图。 符号表示命名空间、 对象、 类、 类成员和其他语言元素。  
  
 可以通过传递到符号库的导航信息确定层次结构中的每个符号[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过以下接口的对象管理器：  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>。  
  
 层次结构中的符号的位置区分符号。 它允许符号浏览工具，以导航到特定的符号。 符号的唯一、 完全限定路径确定的位置。 在路径中的每个元素是一个节点。 路径的顶级节点与开始和结束的特定符号。 例如，如果 M1 方法 C1 类的成员并且 C1 位于 N1 命名空间，M1 方法的完整路径是 N1。C1。M1。 此路径包含三个节点： N1、 C1 和 M1。  
  
 导航信息允许[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对象管理器查找、 选择和保留层次结构中选择符号。 它允许从一个浏览工具导航到另一个。 使用时**对象浏览器**浏览中的符号[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目中，你可以右键单击一种方法，并开始**调用浏览器**工具要在一个调用关系图中显示该方法。  
  
 两种形式描述的符号位置。 规范格式取决于符号的完全限定路径。 它表示层次结构中的唯一位置的符号。 它不依赖于符号浏览工具。 若要获取的规范格式信息，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对象管理器调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>方法。 演示文稿形式描述了在特定的符号浏览工具中的符号的位置。 符号的位置是相对于 hierarchicy 中的其他符号位置。 给定的符号可能有几个演示文稿路径，但只有一个规范路径。 例如，如果 C1 类从 C2 类继承且这两个类位于 N1 命名空间，**对象浏览器**显示以下层次结构树：  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 C2 类，在此示例中的规范路径是 N1 + C2。 C2 的演示文稿路径包括 C1 和"基和接口"节点： N1 + C1 +"基和接口"+ C2。  
  
 若要获取的演示文稿窗体信息对象管理器调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>方法。  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>识别层次结构中的符号  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>若要获取规范和演示文稿窗体的信息  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。  
  
     对象管理器调用此方法以获取包含符号的规范路径中的节点列表。  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。  
  
     对象管理器调用此方法以获取包含符号的演示文稿路径中的节点列表。  
  
## <a name="see-also"></a>另请参阅  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何： 注册与对象管理器的库](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何：向对象管理器公开库提供的符号列表](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)