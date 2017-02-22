---
title: "演练︰ 通过编辑器扩展访问 DTE 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，新的获取 DTE 对象"
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练︰ 通过编辑器扩展访问 DTE 对象
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Vspackage 中，您可以通过调用中获取 DTE 对象 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE 对象的类型的方法。 在 Managed Extensibility Framework \(MEF\) 扩展中，您可以导入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ，然后调用 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 具有一种方法 <xref:EnvDTE.DTE>。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 获取 DTE 对象  
  
#### 若要从该服务提供商获取 DTE 对象  
  
1.  创建一个名为 C\# VSIX 项目 `DTETest`。 添加编辑器分类器项模板并将其命名 `DTETest`。 有关详细信息，请参阅[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
2.  将添加到项目的以下程序集引用︰  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  转到 DTETest.cs 文件并添加以下 `using` 指令︰  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  在 `GetDTEProvider` 类中，导入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  在 `GetClassifier()` 方法中，添加以下代码。  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  如果您需要使用 <xref:EnvDTE80.DTE2> 接口，您可以将 DTE 对象转换为它。  
  
## 请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)