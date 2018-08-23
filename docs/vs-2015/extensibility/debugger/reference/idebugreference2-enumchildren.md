---
title: IDebugReference2::EnumChildren | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 760bad3e67d4ac2100dc0bfa68d319aae18a617d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629193"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu konuda en son sürümünü şu yolda bulunabilir: [IDebugReference2::EnumChildren](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-enumchildren).  
  
Seçili çocuğunu başvuru listesini alın. Daha sonraki kullanımlar için ayrılmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFields`  
 [in] Bayraklarının bir birleşimi [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) hangi alanların numaralandırılmış belirten numaralandırma [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapılardır doldurulmalıdır.  
  
 `dwRadix`  
 [in] Sayısal yedeklenmesine biçimlendirmede kullanılacak sayı tabanı.  
  
 `dwAttribFilter`  
 [in] Bayraklarının bir birleşimi [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) birlikte bir filtre olarak kullanılan sabit listesi `pszNameFilter` sıralanması hangi yapılar seçmek için parametre.  
  
 `pszNameFilter`  
 [in] "Birlikte MyX" gibi bir filtre belirten bir dize `dwAttribFilter` sıralanması yapıları seçmek için parametre.  
  
 `dwTimeout`  
 [in] Bu yöntemden geri dönmeden önce beklenecek milisaniye cinsinden en uzun süre. Kullanım `INFINITE` süresiz bekleme.  
  
 `ppEnum`  
 [out] Döndürür bir [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) istenen alt özellikleri listesini içeren nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Her zaman döndürür `E_NOTIMPL`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
