---
title: "从属性窗口中获取字段说明 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性窗口，字段说明"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 从属性窗口中获取字段说明
在“属性”窗口底部，说明区域显示了与所选属性字段相关的信息。 默认情况下此功能处于开启状态。 如果你想要隐藏说明字段，右键单击“属性”窗口并单击“说明”。 执行此操作还会删除“菜单”窗口中“说明”标题旁的复选标记。 你可以按照将“说明”切换回开启状态的步骤来再次显示该字段。  
  
 说明字段中的信息来自 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每个方法、接口、组件类等在类型库中均可拥有一个未本地化的 `helpstring` 特性。 “属性”窗口从 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> 检索字符串。  
  
### 指定本地化的帮助字符串  
  
1.  将 `helpstringdll` 特性添加到类型库中的库语句（`typelib`）。  
  
    > [!NOTE]
    >  如果类型库位于对象库 \(.olb\) 文件中，则此步骤是可选的。  
  
2.  为字符串指定 `helpstringcontext` 特性。 你还可以指定 `helpstring` 特性。  
  
     这些特性不同于包含在实际 .chm 文件帮助主题中的 `helpfile` 和 `helpcontext` 特性。  
  
 若要检索为突出显示的属性名显示的说明信息，“属性”窗口将为所选属性调用 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>，指定输出字符串的所需 `lcid` 特性。 在内部，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> 查找 `helpstringdll` 特性中指定的 .dll 文件，并在该 .dll 文件上调用 `DLLGetDocumentation` 与指定的内容和 `lcid` 特性。  
  
 `DLLGetDocumentation` 的签名和实现为：  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` 函数必须是在 .def 文件中为 DLL 定义的导出。  
  
 在内部，会创建一个实际为 DLL 的 .olb 文件。 此 DLL 包含一个资源（类型库 \(.tlb\) 文件）和一个导出的函数（`DLLGetDocumentation`）。  
  
 就 .olb 文件而言，`helpstringdll` 特性是可选的，因为它是包含 .tlb 文件本身的同一文件。  
  
 若要获取显示在“说明”窗格中的字符串，为此你至少需要在类型库中指定 `helpstring` 特性。 如果你希望本地化这些字符串，则必须指定 `helpstringdll`（可选）特性和 `helpstringcontext`（必需）特性，并实现 `DLLGetDocumentation`。  
  
 通过 idl 的 `helpstringcontext` 特性和 `DLLGetDocumentation` 获取本地化的信息时，没有需要实现的其他接口。  
  
 获取某一属性的本地化名称和说明的另一方法是实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>。 有关此方法的实现的详细信息，请参阅[属性窗口字段和接口](../extensibility/internals/properties-window-fields-and-interfaces.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [属性窗口字段和接口](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [将属性扩展](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)