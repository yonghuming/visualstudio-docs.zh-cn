---
title: "VSCT XML 架构条件属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0a434800fef7029460854107e79f29a71c75285
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 架构条件属性
条件属性可以应用于所有列表和项。 逻辑运算符和符号扩展表达式计算结果为 true 或 false。 如果为 true，生成的输出中包含的关联的列表或项。  
  
 可以针对其他令牌扩展或常量测试令牌的扩展。 函数 Defined() 用于测试是否已定义特定名称，即使它具有任何值。  
  
 当 Condition 特性应用于列表中时，条件被应用于列表中每个子元素。 如果子元素本身包含的 Condition 属性，然后其条件与相结合的父表达式由 AND 运算。  
  
 1、 '1' 和 'true' 的值计算结果为 true，并且 0、 '0' 和 'false' 计算结果为 false。  
  
## <a name="operators"></a>运算符  
 以下运算符可能用于评估的条件表达式。  
  
|运算符|定义|  
|--------------|----------------|  
|(,)|分组|  
|!|逻辑“非”|  
|\<, >, \<=, >=, ==, !=|关系式与等式|  
|和|Boolean|  
|或|Boolean|  
  
## <a name="examples"></a>示例  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)