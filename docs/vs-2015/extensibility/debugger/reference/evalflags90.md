---
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a95f25f9e970beb31544722b1beeb05b2d480b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156046"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İfade değerlendirmesini denetleyen bayrakların geçerli değerlerini numaralandırır. Bu sabit listesi, [Evalflags](../../../extensibility/debugger/reference/evalflags.md) sabit listesini genişletir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 EVAL90_RETURNVALUE  
 Varsa, dönüş değerinin değerlendirildiğini belirtir.  
  
 EVAL90_NOSIDEEFFECTS  
 Yan etkilere izin verilmeyeceğini belirtir.  
  
 EVAL90_ALLOWBPS  
 Kesme noktalarında durdurmayı belirtir.  
  
 EVAL90_ALLOWERRORREPORT  
 Konağa izin verilecek hata bildirimini belirtir. Birincil olarak Internet Explorer 'da betikte ifade değerlendirmesi için kullanılır.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 İşlevi çağırmak yerine işlevleri adres olarak değerlendirilmeye zorlar.  
  
 EVAL90_NOFUNCEVAL  
 İşlevin değerlendirilmesini engeller. Örneğin, `int` ifadedeki belirteci düşünün `myExpression(int) + 10` . Bu işlev, bir adres olarak doğru şekilde değerlendirilebil, ancak değer olarak değerlendirilemiyor.  
  
 EVAL90_NOEVENTS  
 İfade değerlendirmesi sırasında oluşan olayların, oturum hata ayıklama Yöneticisi 'ne (SDM) veya IDE 'ye gönderilmemesi gerektiğini belirten bayrak.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Tasarım zamanı ifade değerlendirmesini mümkün bir şekilde sunar.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Örtük değişken oluşturulmasına izin verir.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Değerlendirmeyi hemen gerçekleşecek şekilde zorlar. Bu, bir kullanıcıya hizmet verme gibi bir istek sunarken yararlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: Msdbg90. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
