---
title: IDebugObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c179a4443c23373fb92adf522ee0af34acb19c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695265"
---
# <a name="idebugobject"></a>IDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bu arabirim, cildin sembol ve ifade değerlerini kapsüllemek için oluşturduğu bir nesneyi temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir ifade değerlendirici bu arabirimi bir nesneyi temsil etmek için uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, ifade değerlendiricisi tarafından ayrıştırılmış ifadelerde kullanılan tüm nesneler için temel sınıftır. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemi çağrısıyla döndürülür. [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) Bu arabirimden daha özelleştirilmiş arabirimler edinir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugObject` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Nesnenin boyutunu alır.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Nesnenin değerini ardışık bir bayt dizisi olarak alır.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Nesnenin değerini ardışık bir bayt dizisinden ayarlar.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Bu nesnenin başvuru değerini ayarlar.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Nesnenin değerinin adresini temsil eden bellek bağlamını alır.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Hata ayıklama altyapısının adres alanında yönetilen nesnenin bir kopyasını oluşturur.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Bu nesnenin null bir başvuru olup olmadığını sınar.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Bir nesneyi bu ile karşılaştırır.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Bu nesnenin salt okunurdur belirler.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Nesnenin saydam bir ara sunucu olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 İfade değerlendirici bu arabirimi, bir ayrıştırma ağacındaki nesneleri temsil etmek için temel sınıf olarak kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: ee. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade değerlendirme arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Bağla](../../../extensibility/debugger/reference/idebugbinder-bind.md)
