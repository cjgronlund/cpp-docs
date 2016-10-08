---
title: "CW2WEX Class"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
caps.latest.revision: 14
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# CW2WEX Class
This class is used by the string conversion macros `CW2TEX` and `CT2WEX`, and the typedef `CW2W`.  
  
> [!IMPORTANT]
>  This class and its members cannot be used in applications that execute in the Windows Runtime.  
  
## Syntax  
  
```  
  
template<  
   int  t_nBufferLength  
   = 128>  
   class CW2WEX  
  
```  
  
#### Parameters  
 `t_nBufferLength`  
 The size of the buffer used in the translation process. The default length is 128 bytes.  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CW2WEX::CW2WEX](../Topic/CW2WEX::CW2WEX.md)|The constructor.|  
|[CW2WEX::~CW2WEX](../Topic/CW2WEX::~CW2WEX.md)|The destructor.|  
  
### Public Operators  
  
|Name|Description|  
|----------|-----------------|  
|[CW2WEX::operator LPWSTR](../Topic/CW2WEX::operator%20LPWSTR.md)|Conversion operator.|  
  
### Public Data Members  
  
|Name|Description|  
|----------|-----------------|  
|[CW2WEX::m_psz](../Topic/CW2WEX::m_psz.md)|The data member that stores the source string.|  
|[CW2WEX::m_szBuffer](../Topic/CW2WEX::m_szBuffer.md)|The static buffer, used to store the converted string.|  
  
## Remarks  
 Unless extra functionality is required, use `CW2TEX`, `CT2WEX`, or `CW2W` in your code.  
  
 This class contains a fixed-size static buffer which is used to store the result of the conversion. If the result is too large to fit into the static buffer, the class allocates memory using `malloc`, freeing the memory when the object goes out of scope. This ensures that, unlike text conversion macros available in previous versions of ATL, this class is safe to use in loops and that it won't overflow the stack.  
  
 If the class tries to allocate memory on the heap and fails, it will call `AtlThrow` with an argument of **E_OUTOFMEMORY**.  
  
 By default, the ATL conversion classes and macros use the current thread's ANSI code page for the conversion.  
  
 The following macros are based on this class:  
  
-   `CW2TEX`  
  
-   `CT2WEX`  
  
 The following typedef is based on this class:  
  
-   `CW2W`  
  
 For a discussion of these text conversion macros, see [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md).  
  
## Example  
 See [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) for an example of using these string conversion macros.  
  
## Requirements  
 **Header:** atlconv.h  
  
##  <a name="cw2wex__cw2wex"></a>  CW2WEX::CW2WEX  
 The constructor.  
  
```  
  
CW2WEX(  
      LPCWSTR  psz,  
      UINT  nCodePage  
   ) throw(...);  
   CW2WEX(  
      LPCWSTR  psz  
    ) throw(...);  
  
```  
  
### Parameters  
 `psz`  
 The text string to be converted.  
  
 `nCodePage`  
 The code page. Not used in this class.  
  
### Remarks  
 Creates the buffer required for the translation.  
  
##  <a name="cw2wex___dtorcw2wex"></a>  CW2WEX::~CW2WEX  
 The destructor..  
  
```  
  
~CW2WEX( ) throw( );  
  
```  
  
### Remarks  
 Frees the allocated buffer.  
  
##  <a name="cw2wex__m_psz"></a>  CW2WEX::m_psz  
 The data member that stores the source string.  
  
```  
  
LPWSTR m_psz;  
  
```  
  
##  <a name="cw2wex__m_szbuffer"></a>  CW2WEX::m_szBuffer  
 The static buffer, used to store the converted string.  
  
```  
  
wchar_t m_szBuffer[ t_nBufferLength  
   ];  
  
```  
  
##  <a name="cw2wex__operator_lpwstr"></a>  CW2WEX::operator LPWSTR  
 Cast operator.  
  
```  
  
operator LPWSTR( ) const throw( );  
  
```  
  
### Return Value  
 Returns the text string as type `LPWSTR`.  
  
## See Also  
 [CA2AEX Class](../VS_visualcpp/CA2AEX-Class.md)   
 [CA2CAEX Class](../VS_visualcpp/CA2CAEX-Class.md)   
 [CA2WEX Class](../VS_visualcpp/CA2WEX-Class.md)   
 [CW2AEX Class](../VS_visualcpp/CW2AEX-Class.md)   
 [CW2CWEX Class](../VS_visualcpp/CW2CWEX-Class.md)   
 [Class Overview](../VS_visualcpp/ATL-Class-Overview.md)