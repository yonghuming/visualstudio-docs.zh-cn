---
title: "MSBuild 的条件构造 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Choose> 元素 [MSBuild]"
  - "<Otherwise> 元素 [MSBuild]"
  - "<When> 元素 [MSBuild]"
  - "Choose 元素 [MSBuild]"
  - "条件构造 [MSBuild]"
  - "MSBuild, 条件构造"
  - "Otherwise 元素 [MSBuild]"
  - "When 元素 [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# MSBuild 的条件构造
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 使用 [Choose](../msbuild/choose-element-msbuild.md)、[When](../msbuild/when-element-msbuild.md) 和 [Otherwise](../msbuild/otherwise-element-msbuild.md) 元素提供一种处理 either\/or 的机制。  
  
## 使用 Choose 元素  
 `Choose` 元素包含一系列具有 `Condition` 特性的 `When` 元素，将按从上至下的顺序测试这些元素，直到某个元素的计算结果为 `true` 为止。  如果不止一个 `When` 元素的计算结果为 `true`，将仅仅使用第一个元素。  如果 `When` 元素中没有一个条件的计算结果为 `true`，将计算 `Otherwise` 元素（如果存在的话）。  
  
 `Choose` 元素可以用作 `Project`、`When` 和 `Otherwise` 元素的子元素。  `When` 和 `Otherwise` 元素可以有 `ItemGroup`、`PropertyGroup` 或 `Choose` 子元素。  
  
## 示例  
 下面的示例对 either\/or 处理使用 `Choose` 和 `When` 元素。  项目的属性和项是根据 `Configuration` 属性的值设置的。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## 请参阅  
 [Choose 元素 \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [When 元素 \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Otherwise 元素 \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)