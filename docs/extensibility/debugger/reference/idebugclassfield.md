---
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734294"
---
# <a name="idebugclassfield"></a>IDebugClassField
Bu arabirim bir sınıfı tür olarak temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan aynı nesne üzerinde uygular. Bu arabirim, bir sınıf türünü temsil eden bir özelleşmenin bir özelleştirmesi.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir dizi arabirimde [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)dahil bu arabirimi döndürebilirler. Ayrıca, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi bayrağını döndürürse, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface](/cpp/atl/queryinterface) 'i de kullanabilirsiniz `FIELD_TYPE_CLASS` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdakileri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Bu sınıfın temel sınıfları için bir Numaralandırıcı oluşturur.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Sınıfta belirli bir arabirimin tanımlanıp tanımlanamayacağını belirler.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Bu sınıfın iç içe sınıfları için bir Numaralandırıcı oluşturur.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Bu sınıfı kapsayan sınıfı alır.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Bu sınıf tarafından uygulanan arabirimler için bir Numaralandırıcı oluşturur.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Bu sınıfın oluşturucuları için bir Numaralandırıcı oluşturur.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Varsayılan dizin oluşturucunun adını alır.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Bu sınıfın iç içe geçmiş numaralandırıcıları için bir Numaralandırıcı oluşturur.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
