---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac8910ebe012e1edbaa6c26695027214db4e66c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462136"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Uygulamanın veya bağlı modülün kaynak kodu dilini belirtir.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Öğeler
CV_CFL_C uygulama dili C 'dir.

CV_CFL_CXX uygulama dili C++ ' dır.

CV_CFL_FORTRAN uygulama dili FORTRAN.

CV_CFL_MASM uygulama dili Microsoft Macro Assembler ' dur.

CV_CFL_PASCAL uygulama dili Pascal.

CV_CFL_BASIC uygulama dili temel.

Uygulama dili CV_CFL_COBOL COBOL.

CV_CFL_LINK uygulama bağlayıcı tarafından oluşturulan bir modüldür.

CV_CFL_CVTRES uygulama, CVTRES aracıyla dönüştürülen bir kaynak modülüdür.

CV_CFL_CVTPGD uygulama, CVTPGD aracı ile oluşturulmuş bir POGO iyileştirilmiş modüldür.

CV_CFL_CSHARP uygulama dili C# ' dir.

CV_CFL_VB uygulama dili Visual Basic.

CV_CFL_ILASM uygulama dili, ara dil derlemesi (yani, ortak dil çalışma zamanı (CLR) derlemesi).

CV_CFL_JAVA uygulama dili Java.

CV_CFL_JSCRIPT uygulama dili JScript.

CV_CFL_MSIL uygulama dili bilinmeyen bir Microsoft ara dili (MSIL), büyük olasılıkla [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation) anahtarını kullanmanın bir sonucudur.

CV_CFL_HLSL uygulama dili yüksek düzey gölgelendirici dilidir.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) metoduna yapılan bir çağrı tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
