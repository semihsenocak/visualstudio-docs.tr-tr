---
title: 'IDiaEnumLineNumbers:: get__NewEnum | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 409f0234c4dbe81f6be0928caf458839baa2cefb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190121"
---
# <a name="idiaenumlinenumbersget__newenum"></a>IDiaEnumLineNumbers::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>Bu Numaralandırıcı sürümünü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pRetVal  
 dışı `IUnknown` Bu Numaralandırıcı sürümünü temsil eden arabirimi döndürür <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
