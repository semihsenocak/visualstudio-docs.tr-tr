---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f23c2ad4aeaf911e45b28686584d741e5c4d22f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704132"
---
# <a name="idebugbinder3"></a>IDebugBinder3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bu arabirim, türlere, diğer adlara ve özel Görselleştirici hizmetlerine erişim sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir hata ayıklama altyapısı, bu arabirimi diğer adları, özel görselleştiricisi hizmetlerini ve nesne türü bilgilerine erişimi desteklemek için uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bir [ıdebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi bu arabirimi [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)kullanarak edinir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi tarafından sunulan yöntemlerin yanı sıra, bu arabirim şunları uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Bu nesnenin bağlandığı belleği temsil eden bir bellek nesnesi alır.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Bu nesneyle ilişkili özel durumu alır (varsa),|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Adı verilen bir diğer ad alır,|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Bu nesne için tüm diğer adların bir dizisini alır,|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Bu nesneyle ilişkili bağımsız değişken türlerinin sayısını alır,|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Bu nesneyle ilişkili bağımsız değişken türlerinin bir listesini alır,|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Görselleştirici hizmetine bir arabirim alır,|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Bir nesne konumu ya da 64 bitlik bir bellek adresini bir bellek bağlamına dönüştürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: ee. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade değerlendirme arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
