---
title: "VSCT XML 架构条件属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素，条件属性"
  - "条件属性 (VSCT XML 架构)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# VSCT XML 架构条件属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

条件属性可以应用于所有列表和项。 逻辑运算符和符号扩展表达式计算结果为 true 或 false。 如果为 true，关联的列表项包含在生成的输出。  
  
 可以针对其他令牌的扩展或常量测试令牌的扩展。 函数 Defined\(\) 用于测试是否定义了特定名称，即使它没有任何价值。  
  
 当条件属性应用于列表中时，该条件适用于列表中每个子元素。 如果子元素本身包含条件属性，然后其条件与相结合的父表达式由 AND 运算。  
  
 值 1、 '1' 和 'true' 的计算结果为 true，和 0、 '0' 和 'false' 计算结果为 false。  
  
## 运算符  
 以下运算符可用于计算条件表达式的值。  
  
|运算符|定义|  
|---------|--------|  
|\(,\)|分组|  
|\!|逻辑“非”|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|关系和相等性|  
|和|Boolean|  
|或|Boolean|  
  
## 示例  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)