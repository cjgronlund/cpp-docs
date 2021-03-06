---
title: "Platform::ValueType Class | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"  
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ValueType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ValueType Class"
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Platform::ValueType Class
The base class for instances of value types.  
  
## Syntax  
  
```cpp  
public ref class ValueType : Object  
```  
  
## Public methods  
  
|||  
|-|-|  
|[ValueType::ToString Method](#tostring)|Returns a string representation of the object. Inherited from [Platform::Object](../cppcx/platform-object-class.md).|  
  
### Remarks  
 The ValueType class is used to construct value types. ValueType is derived from Object, which has basic members. However, the compiler detaches those basic members from value types that are derived from the ValueType class. The compiler reattaches those basic members when a value type is boxed.  
  
### Requirements  
 **Minimum supported client:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Minimum supported server:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Namespace:** Platform  
  
 **Metadata:** platform.winmd  

## <a name="tostring"></a> ValueType::ToString Method
Returns a string representation of the object.  
  
### Syntax  
  
```cpp  
Platform::String ToString();  
```  
  
### Return Value  
 A Platform::String that represents the value.  
    
## See Also  
 [Platform namespace](../cppcx/platform-namespace-c-cx.md)