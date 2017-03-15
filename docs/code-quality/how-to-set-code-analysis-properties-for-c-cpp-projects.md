---
title: "如何：设置 C/C++ 项目的代码分析属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "C/C++ 代码分析属性"
  - "代码分析属性"
  - "属性, C/C++ 代码分析"
  - "属性, 代码分析"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：设置 C/C++ 项目的代码分析属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以配置代码分析工具使用哪些规则分析项目的每个配置中的代码。  此外，还可以指示代码分析禁止显示由第三方工具生成并添加到项目的代码中的警告。  
  
## “代码分析”属性页  
 **“代码分析”**属性页包含项目的所有代码分析配置设置。  若要在**“解决方案资源管理器”**中打开项目的“代码分析”属性页，请右击该项目，然后单击**“属性”**。  然后，展开**“配置属性”**，再选择**“代码分析”**选项卡。  
  
## 项目配置和平台  
 通过**“配置”**列表和**“平台”**列表，可以对不同的项目配置和平台组合应用不同的代码分析设置。  例如，可以指示代码分析对项目的调试版本应用一组规则，而对发布版本应用一组不同的规则。  
  
## 启用代码分析  
 通过选择**“生成时启用 C\/C\+\+ 代码分析”**，可以决定是否为项目启用代码分析。  例如，在与**“配置”**列表结合使用时，可以决定为调试版本禁用代码分析，而为发布版本启用代码分析。  
  
 如果项目包含托管代码，则通过选择**“生成时启用代码分析”**，可以决定是启用还是禁用代码分析。  
  
 代码分析旨在帮助您提高代码的质量，并避免常见的缺陷。  因此，请仔细考虑是否禁用代码分析。  通常，最好禁用不希望应用于项目的规则集或单个规则。  
  
## 生成的代码  
 开发人员通常使用工具来加快应用程序的开发。  这些工具可以生成添加到项目的代码。  您可能希望看到代码分析在所生成代码中发现的规则冲突。  但是，如果不想维护代码，您可能不希望看到规则冲突。  
  
 通过**“常规”**属性页上的**“禁止显示所生成代码的结果”**复选框，可以选择是否希望看到第三方工具生成的托管代码产生的代码分析警告。  
  
## 规则集  
 如果项目包含托管代码，则通过从**“运行此规则集”**列表选择规则集，可选择代码分析中要应用的规则。  
  
## 请参阅  
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C\/C\+\+ 代码分析警告](../code-quality/code-analysis-for-c-cpp-warnings.md)