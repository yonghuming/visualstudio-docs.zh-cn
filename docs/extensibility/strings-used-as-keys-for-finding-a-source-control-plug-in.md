---
title: "字符串用作键用于查找源代码管理插件 | Microsoft Docs"
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
  - "源代码管理插件，用于查找的字符串"
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 字符串用作键用于查找源代码管理插件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以下字符串是用于访问注册表，以查找有关源代码管理信息插件密钥。  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, ，`STR_SCCPROVIDERPATH`, ，和 `STR_SCCPROVIDERNAME` 注册表项或值，用于将一个 DLL 注册为 Visual Studio 源代码管理插件。  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, ，`SCC_KEY, SCC_FILE_SIGNATURE`, ，和 `SCC_STATUS_FILE` 用于描述 MSSCCPRJ 的格式。源代码管理文件。  
  
## 字符串键和值  
  
|键|值|  
|-------|-------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|源代码管理|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC\_Project\_Name|  
|`SCC_PROJECTAUX_KEY`|SCC\_Aux\_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ。源代码管理|  
|`SCC_KEY`|源代码管理|  
|`SCC_FILE_SIGNATURE`|源代码控制文件|  
|`SCC_NSE`|命名空间扩展|  
|`SCC_NSE_PREFIX`|Protocal 前缀|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\\Microsoft\\SourceSafe|  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [如何: 安装了源代码管理插件](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ。源代码管理文件](../extensibility/mssccprj-scc-file.md)