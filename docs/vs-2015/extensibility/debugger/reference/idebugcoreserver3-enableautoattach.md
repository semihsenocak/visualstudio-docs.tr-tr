---
title: 'IDebugCoreServer3:: Enableoto Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45362c9456b99d6cec0af01dcb29844d02363a27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569801"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirtilen hata ayıklama motorları için otomatik eklemeye izin vermez.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rgguidSpecificEngines`  
 'ndaki Her hata ayıklama altyapısının otomatik iliştirme olarak işaretleneceği GUID dizisi.  
  
 `celtSpecificEngines`  
 'ndaki İçinde belirtilen altyapı sayısı `rgguidSpecificEngines` .  
  
 `pszStartPageUrl`  
 'ndaki Otomatik iliştirme sırasında kullanılacak başlangıç URL 'SI.  
  
 `pbstrSessionID`  
 dışı Otomatik olarak eklenen oturumun KIMLIĞI.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. Bir hata kodu `E_AUTO_ATTACH_NOT_REGISTERED` , otomatik iliştirme sınıf fabrikasının kaydedilmemiş olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen URL ile ilişkili bir program başlatıldığında, belirtilen hata ayıklama motorları otomatik olarak başlatılır ve eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
