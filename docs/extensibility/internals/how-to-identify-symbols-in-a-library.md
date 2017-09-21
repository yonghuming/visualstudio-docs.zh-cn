---
title: "如何: 确定库中的符号 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调用浏览器工具，用于标识库中的符号"
  - "调用浏览器工具"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何: 确定库中的符号
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

符号符号浏览工具显示分层视图。  符号表示命名空间、对象、类、类成员和其他语言元素。  
  
 在层次结构中每个符号可由符号库传递的导航信息来确定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器以下接口:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 符号的位置在层次结构中区分个符号。  它允许符号浏览工具导航到特定符号。  符号的唯一，完全限定路径确定位置。  路径中的每个元素都是节点。  路径从顶部节点和结束启动与特定符号。  例如，在中，如果该 M1 方法是 C1 类的成员，并且 C1 在 N1 命名空间，则与方法的完整路径为 N1。C1。与.  此路径包含三个节点:N1、 C1 和 M1。  
  
 导航信息允许 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器中，选择，并保留选择了在层次结构的符号。  它允许在从一个工具浏览到另一个。  当使用 **对象浏览器** 浏览 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 符号时项目中，可以右击方法和启动 **调用浏览器** 工具显示在调用关系图的方法。  
  
 两种形式描述符号位置。  规范格式基于符号的完全限定路径。  它表示符号的一个位置在层次结构。  它是符号浏览和独立。  若要获取规范格式窗体信息， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。  表示形式描述符号的位置在特定符号浏览工具中的。  符号的位置相对于其他符号的位置。 hierarchicy。  特定符号只能有若干表示路径，但是，一个规范路径。  例如，因此，如果 C1 类从 C2 类继承，并且类在 N1 命名空间， **对象浏览器** 显示以下分层树:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 C2 类规范路径，在此示例中，是 N1 \+ C2。  C2 表示路径包括 C1 和 “foundation 和接口”节点:N1 \+ C1 \+ “foundation 和接口” \+ C2。  
  
 若要获取表示形式信息，对象管理器调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。  
  
## 标识在层次结构中的符号  
  
#### 获取规范和表示形式信息  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。  
  
     对象管理器调用此方法来获取该符号规范路径包含的节点列表。  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。  
  
     对象管理器调用此方法来获取该符号表示路径包含的节点列表。  
  
## 请参阅  
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何: 注册库与对象管理器](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何: 公开库对对象管理器提供的符号列表](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)