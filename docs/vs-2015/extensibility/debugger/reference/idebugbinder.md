---
title: Idebugciltçi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc00c50e3c340ab0685ab1010c6e924e77a18a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782819"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bu arabirim, genellikle sembol sağlayıcısı tarafından döndürülen bir sembol alanını, simgenin geçerli değerini içeren bir bellek bağlamına veya nesnesine bağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirim, ifade değerlendirmesini destekler ve hata ayıklama altyapısı (DE) tarafından uygulanmalıdır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, ifade değerlendirmesi sürecinde kullanılır ve genellikle [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)uygulamalarında kullanılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBinder` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Bağladığınızda](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Simgenin geçerli değerini içeren bellek bağlamını veya nesnesini alır.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bir nesnenin çalışma zamanı türünü belirler.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Bir nesne konumunu veya bellek adresini bir bellek bağlamına dönüştürür.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|İşlev parametreleri oluşturmak için kullanılan bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi alır.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Bir değişkenin tam türünü alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, ayrıştırma ağaçlarında ifade değerlendiricisi tarafından kullanılan nesneleri döndürür. İfade değerlendirici, ifadedeki sembolleri, her bir sembolü kaynak koddaki türü ve konumu bakımından açıklayan [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)örneklerine dönüştürmek için sembol sağlayıcısını kullanarak bir ifadeyi ayrıştırır. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemi nesneleri, `IDebugField` bir sembol türünü, bellekteki gerçek bir değere bağlayan veya bağlayan [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerine dönüştürür. `IDebugObject`Daha sonra bu nesneler daha sonra değerlendirme için bir ayrıştırma ağacında depolanır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: ee. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade değerlendirme arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
