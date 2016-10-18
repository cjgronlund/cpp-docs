---
title: "&lt;paramref&gt; (Visual C++)"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "paramref"
  - "<paramref>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "paramref C++ XML tag"
  - "<paramref> C++ XML tag"
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
caps.latest.revision: 9
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# &lt;paramref&gt; (Visual C++)
The \<paramref> tag gives you a way to indicate that a word is a parameter. The .xml file can be processed to format this parameter in some distinct way.  
  
## Syntax  
  
```  
<paramref name="name"/>  
```  
  
#### Parameters  
 `name`  
 The name of the parameter to refer to.  Enclose the name in single or double quotation marks.  The compiler issues a warning if it does not find `name`.  
  
## Remarks  
 Compile with [/doc](../buildref/-doc--process-documentation-comments---c-c---.md) to process documentation comments to a file.  
  
## Example  
  
```  
// xml_paramref_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_paramref_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// The <paramref name="Int1"/> parameter takes a number.  
   /// </summary>  
   void MyMethod(int Int1) {}  
};  
```  
  
## See Also  
 [XML Documentation](../ide/xml-documentation--visual-c---.md)