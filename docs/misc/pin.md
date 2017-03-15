---
title: "__pin | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "钉住指针，__pin 关键字"
  - "非托管类型"
  - "__pin 关键字"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
**注意** 本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [pin\_ptr \(C\+\+\/CLI\)](/visual-cpp/windows/pin-ptr-cpp-cli) 有关新语法中使用的等效功能的信息。  
  
 在垃圾回收过程中，请防止公共语言运行时移动托管类的对象或嵌入对象。  
  
## 语法  
  
```  
  
__pin   
identifier  
  
```  
  
## 备注  
 `__pin` 关键字可声明指向托管类的对象或嵌入对象的指针和防止公共语言运行时在垃圾回收期间移动该对象。 当向非托管函数传递托管类的地址时，这很有用，因为在解析非托管函数调用的过程中，该地址不会意外更改。  
  
 固定指针在其词法范围内仍然有效。 一旦固定指针超出范围，对象就不再被视为固定（当然，除非存在其他指向或接入对象的固定指针）。  
  
 MSIL 没有“块范围”的概念 – 所有局部变量位于函数范围内。 为了告知系统固定不再有效，编译器将生成将 NULL 分配给固定指针的代码。 如果您需要在不离开块的情况下取消固定对象，那么就可以自行完成上述操作。  
  
 不应将固定指针转换为非托管指针，并且不应在对象不再固定后（在固定指针超出范围后）继续使用此非托管指针。 与 gc 指针不同，固定指针可以转换为未托管的非 gc 指针。 但是，在使用非托管指针时，用户要负责保持固定。  
  
 使用固定指针获取变量的地址，然后在固定指针超出范围后使用该地址，这样的操作不应执行。  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 以下示例显示了正确行为：  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## 示例  
 在以下示例中，`pG` 指向的对象被固定，直到它超出范围：  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## 输出  
  
```  
1  
```