---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738118"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Bekleyen ve bağlantılı kesme noktaları için kesme noktası koşul stilini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Alanlar
`BP_COND_NONE`\
Kesme noktasının konumuna ulaşıldığında kesme noktası ateşlenir. Kesme noktası koşulu belirtilmedi.

`BP_COND_WHEN_TRUE`\
Kesme noktası yalnızca kesme noktasıyla ilişkili koşullu ifade olarak değerlendirildiğinde ateşlenir `true` .

`BP_COND_WHEN_CHANGED`\
Kesme noktası yalnızca kesme noktasıyla ilişkili koşullu ifadenin değeri önceki değerlendirmeden değiştirildiğinde harekete geçirilir.

## <a name="remarks"></a>Açıklamalar
`styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) yapısının üyesi için kullanılır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
