---
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200235"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Geçerli belge konumunun aralığını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwBegOffset`  
 [in, out] Aralığın başlangıç konumunun konumu. Bu bilgi gerekmiyorsa bu parametreyi null değeri olarak ayarlayın.  
  
 `pdwEndOffset`  
 [in, out] Aralığın bitiş konumunun konumu. Bu bilgi gerekmiyorsa bu parametreyi null değeri olarak ayarlayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir konum kesme noktası için bir belge konumunda belirtilen Aralık, aslında koda katkıda bulunan bir ifadenin önünde aramak için hata ayıklama altyapısı (DE) tarafından kullanılır. Örneğin, aşağıdaki kodu göz önünde bulundurun:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 5. satır hata ayıklamakta olan programa kod vermez. 5. satırda kesme noktasını ayarlayan hata ayıklayıcı, kod katkıda bulunan ilk satır için belirli bir miktarı ileri doğru aramak isterse, hata ayıklayıcı, bir kesme noktasının doğru şekilde yerleştirilebileceği ek aday çizgileri içeren bir Aralık belirler. Ayrıca, bir kesme noktası kabul edebilecek bir çizgi bulunana kadar bu satırlarda ileriye doğru arama yapılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
