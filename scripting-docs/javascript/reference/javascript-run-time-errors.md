---
title: "JavaScript 运行时错误 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT-32725"
  - "VS.WebClient.Help.SCRIPT7002"
  - "VS.WebClient.Help.SCRIPT1001"
  - "VS.WebClient.Help.SCRIPT16389"
  - "VS.WebClient.HelpSCRIPT50"
  - "VS.WebClient.HelpSCRIPT70"
  - "VS.WebClient.HelpSCRIPT87"
  - "VS.WebClient.HelpSCRIPT65535"
  - "VS.WebClient.HelpSCRIPT445"
  - "VS.WebClient.HelpSCRIPT600"
  - "VS.WebClient.HelpSCRIPT2343"
  - "VS.WebClient.HelpSCRIPT122"
  - "VS.WebClient.HelpSCRIPT28"
  - "VS.WebClient.HelpSCRIPT16386"
  - "VS.WebClient.HelpSCRIPT7015"
  - "VS.WebClient.HelpSCRIPT3"
  - "VS.WebClient.HelpSCRIPT16388"
  - "VS.WebClient.HelpSCRIPT14"
  - "VS.WebClient.HelpSCRIPT12030"
  - "VS.WebClient.HelpSCRIPT12029"
  - "VS.WebClient.HelpSCRIPT1001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "错误 [JavaScript]"
  - "运行时错误, JavaScript"
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# JavaScript 运行时错误
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行时错误是指当你的脚本尝试执行系统无法执行的操作时发生的错误。 在计算变量表达式或分配内存时，你可能会看到运行时错误。  
  
## Windows 运行时错误  
 如果你正在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中使用 Windows 运行时 API，你可能会看到从 Windows Runtime HRESULT 转换而来的 JavaScript 错误。 超过 0x80070000 范围的 Windows 运行时 HRESULT 将通过采用低位的十六进制值，然后将该值转换为十进制来转换为 JavaScript 错误。 例如，HRESULT 0x80070032 将转换为十进制值 50，因此 JavaScript 错误为 SCRIPT50。 HRESULT 0x80074005 将转换为十进制值 16389，因此 JavaScript 错误为 SCRIPT16389。  
  
## 错误  
  
|错误号|描述|  
|---------|--------|  
|5|[拒绝访问](../../javascript/misc/access-is-denied.md)|  
|438|[对象不支持此属性或方法](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|内存不足|  
|5029|[数组长度必须为有限正整数](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[数组长度必须赋值为有限正数](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[缺少 Array 或 arguments 对象](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[缺少布尔值](../../javascript/misc/boolean-expected.md)|  
|5003|[无法给函数结果赋值](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[无法给“this”赋值](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[不支持在值参数中进行循环引用](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[缺少日期对象](../../javascript/misc/date-object-expected.md)|  
|5015|[缺少枚举器对象](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[引发了异常且未被捕获](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[正则表达式中缺少“\)”](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[正则表达式中缺少“&#93;”](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[函数没有有效的原型对象](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[缺少函数](../../javascript/misc/function-expected.md)|  
|5008|[非法赋值](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[字符集的范围无效](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[无效的替换器参数](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[缺少 JavaScript 对象](../../javascript/misc/javascript-object-expected.md)|  
|5001|[缺少数字](../../javascript/misc/number-expected.md)|  
|5007|[缺少对象](../../javascript/misc/object-expected.md)|  
|5012|[缺少对象成员](../../javascript/misc/object-member-expected.md)|  
|5016|[缺少正则表达式对象](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[缺少字符串](../../javascript/misc/string-expected.md)|  
|5017|[正则表达式中存在语法错误](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[小数位数超出范围](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[精度超出范围](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[要解码的 URI 不是有效编码](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[要编码的 URI 包含无效字符](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[未定义标识符](../../javascript/misc/undefined-identifier.md)|  
|5018|[意外的限定符](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[缺少 VBArray](../../javascript/misc/vbarray-expected.md)|  
  
## 请参阅  
 [JavaScript 语法错误](../../javascript/reference/javascript-syntax-errors.md)