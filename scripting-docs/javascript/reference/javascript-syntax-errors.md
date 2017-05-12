---
title: "JavaScript 语法错误 | Microsoft Docs"
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
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "错误 [JavaScript]"
  - "语法错误，JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# JavaScript 语法错误
当某个 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 语句中的结构违反一个或多个语法规则时，会出现 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 语法错误。  
  
## 错误  
  
|错误号|说明|  
|---------|--------|  
|1019|[“break”不能位于循环外](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[“continue”不能位于循环外](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[条件编译已关闭](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|[“default”在“switch”语句中只能出现一次](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[应为“\(”](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[应为“\)”](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[应为“\/”](../../javascript/misc/expected-minus.md)|  
|1003|[应为“:”](../../javascript/misc/expected-colon.md)|  
|1004|[应为“;”](../../javascript/misc/expected-semicolon.md)|  
|1032|[应为“@”](../../javascript/misc/expected-at.md)|  
|1029|[应为“@end”](../../javascript/misc/expected-at-end.md)|  
|1007|[应为“&#93;”](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[应为“{”](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[应为“}”](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[应为“\=”](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[应为“catch”](../../javascript/misc/expected-catch.md)|  
|1031|[应为常量](../../javascript/misc/expected-constant.md)|  
|1023|[应为十六进制数字](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[应为标识符](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[应为标识符、字符串或数字](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[应为“while”](../../javascript/misc/expected-while.md)|  
|1014|[无效字符](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[未找到标签](../../javascript/misc/label-not-found.md)|  
|1025|[标签已重定义](../../javascript/misc/label-redefined.md)|  
|1018|[“return”语句在函数范围外](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[语法错误](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Throw 的后面必须在同一源行跟有一个表达式](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[未终止的注释](../../javascript/misc/unterminated-comment.md)|  
|1015|[未终止的字符串常量](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### 脚本宿主错误  
 确切的说，以下错误是与脚本宿主有关的错误，但您可能有时会看到这些错误。  
  
|错误|HRESULT|说明|  
|--------|-------------|--------|  
|SCRIPT\_E\_RECORDED|0x86664004|已记录错误以便在脚本引擎和主机之间传递。  主机需要将错误代码传递给调用方。|  
|SCRIPT\_E\_REPORTED|0x80020101|脚本引擎已通过 IActiveScriptSite::OnScriptError 将未经处理的异常报告给主机。  主机可忽略此错误。|  
|SCRIPT\_E\_PROPAGATE|0x8002010|脚本错误将传播到可能位于其他线程中的调用方。  主机应将错误代码传递给调用方。|  
  
## 请参阅  
 [JavaScript 运行时错误](../../javascript/reference/javascript-run-time-errors.md)