---
title: "通常用于扩展项目的对象的 Catid | Microsoft Docs"
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
  - "Vspackage Catid"
  - "Guid、 Vspackage"
  - "Vspackage 的 Catid"
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 通常用于扩展项目的对象的 Catid
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下表列出了用于扩展 `Project` 和 `ProjectItem` 自动化对象 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目的 CATIDs。  这些 CATIDs 在 VSLangProj.olb 定义。  
  
## 列表 CATIDs  
  
|名称|GUID|  
|--------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614\-D0D5\-11D2\-8599\-006097 C68 E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615\-D0D5\-11D2\-8599\-006097 C68 E81}|  
  
## Visual Basic CATIDs  
 下表列出了用于扩展 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 浏览对象的 CATIDs。  它们都在 VSLangProj.olb 定义。  
  
|名称|GUID|  
|--------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FD C879 \- C32 A\-4751\-A3D3\-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11\-14EB\-489b\-87F0\-F01 C52 AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D\-3 C72 \-40A5\-95A0\-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932D C619 \-2EAA\-4192\-B7E6\-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{} 2289B812\-8191\-4e81\-B7B3\-174045AB0 CB5|  
  
## Visual C\# CATIDs  
 下面 CATIDs 可用于扩展 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 浏览对象。  它们都在 VSLangProj.olb 定义。  
  
|名称|GUID|  
|--------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{} 4EF9F003\-DE95\-4d60\-96B0\-212979F2A857|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12 CE10 A\-227F\-4963\-ADB6\-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF\-ED4E\-48B0\-8 C7 B\- C74 EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278\-054A\-45DB\-BF9E\-5F22484 CC84 C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8\- C855 \-4a4e\-95A5\- CB45 C67 D6 C27}|  
  
## C\+\+ CATIDs  
 下面 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目系统 CATIDs 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 的类型库代码中并未显示 2003 年并且必须包括时，就要扩展这些项的对象。  这些 CATIDs 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]最新版本的类型库中包括的内容。  
  
|名称|GUID|  
|--------|----------|  
|`CVCProjectNode`|{} EE8299CB\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFolderNode`|{} EE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFileNode`|{EE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
  
 下面的代码示例演示如何这些过程演示在代码中 CATIDs。  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 下面 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目系统 CATIDs 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 的类型库在代码或显示 2003 年并且必须包括时，就要扩展这些项的对象。  这些 CATIDs 只能在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 和 visual studio 将无法在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]最新版本。  
  
|名称|GUID|  
|--------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE\-20A7\-48e4\-A CA1 \-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3\- C60 A\-44f4\-A74B\-14 C90 EF9CACE}|  
|`CVCReferences`|{} FE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
  
 下面的代码示例演示如何对这些程序代码中的 CATIDs:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项类型的 GUID 如下表所示。  
  
|项目类型|GUID|  
|----------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{FAE04E C0 \-301F\-11D3\-BF4B\-00 C04 F79EFBC}|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F}|  
  
## 请参阅  
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)