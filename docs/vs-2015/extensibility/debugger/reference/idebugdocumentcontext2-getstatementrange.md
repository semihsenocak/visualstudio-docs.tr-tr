---
title: 'IDebugDocumentContext2:: GetStatementRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68411ac4ded03c83ad0ad1e414107e6591f4e975
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145055"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belge bağlamının dosya deyimleri aralığını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetStatementRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetStatementRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBegPosition`  
 [in, out] Başlangıç konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.  
  
 `pEndPosition`  
 [in, out] Bitiş konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade aralığı, bu belge bağlamının başvurduğu koda katkıda bulunan satırların aralığıdır.  
  
 Bu belge bağlamı içindeki kaynak kodu aralığını (açıklamalar dahil) almak için [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) yöntemini çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `CDebugContext` [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir. Bu örnek, yalnızca başlangıç konumu null değer değilse bitiş konumunu doldurur.  
  
```cpp#  
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,  
                                         TEXT_POSITION* pEndPosition)    
{    
   HRESULT hr;    
  
   // Check for a valid beginning position argument pointer.    
   if (pBegPosition)    
   {    
      // Copy the member TEXT_POSITION into the local pBegPosition.    
      memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));    
  
      // Check for a valid ending position argument pointer.   
     if (pEndPosition)    
      {    
         // Copy the member TEXT_POSITION into the local pEndPosition.    
         memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
