---
title: POPLISTFUNC | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8b193eae0e41f48c0f947bbf8af596084a1544f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42693631"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda en son sürümünü şu yolda bulunabilir: [POPLISTFUNC](https://docs.microsoft.com/visualstudio/extensibility/poplistfunc).  
  
Bu geri çağırma için sağlanan [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE tarafından ve kaynak denetimi eklentisi tarafından bir dosya veya dizinlerin listesini güncelleştirmek için kullanılır (Ayrıca sağlanan `SccPopulateList` işlevi).  
  
 Ne zaman bir kullanıcının seçtiği **alma** komut IDE'de IDE kullanıcı alabileceği tüm dosyaların bir liste kutusu görüntüler. Ne yazık ki, IDE kullanıcı alabilirsiniz tüm dosyaların tam listesini bilmez; Bu liste yalnızca eklenti vardır. Diğer kullanıcılar için kaynak kodu denetim projesinin dosyaları eklediyseniz, bu dosyalar, listede görünmesi gerekir, ancak IDE bunları hakkında bilmez. IDE kullanıcı alabilirsiniz gördüğü dosyaların bir listesini oluşturur. Kullanıcıya bu listeyi gösterir önce çağrılır [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` kaynak denetimi eklentisi vererek eklemek ve dosyaları listeden silmek için bir fırsat.  
  
## <a name="signature"></a>İmza  
 Kaynak Denetimi Eklentisi aşağıdaki prototipe sahip bir IDE uygulanan işlevi çağrılarak listenin değiştirir:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 pvCallerData  
 `pvCallerData` Parametresi için (IDE) çağıran tarafından geçirilen [SccPopulateList](../extensibility/sccpopulatelist-function.md). Kaynak Denetimi Eklentisi bu parametrenin içeriği hakkında hiçbir şey varsaymanız gerekir.  
  
 fAddRemove  
 Varsa `TRUE`, `lpFileName` dosya listesine eklenmesi gereken bir dosyadır. Varsa `FALSE`, `lpFileName` dosya listesinden silinmesi gereken bir dosyadır.  
  
 nStatus  
 Durumunu `lpFileName` (bir birleşimini `SCC_STATUS` BITS; bkz: [dosya durum kodu](../extensibility/file-status-code-enumerator.md) Ayrıntılar için).  
  
 lpDosyaAdı  
 Dosya adı eklemek veya listeden silmek için tam dizin yolu.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`TRUE`|Eklenti bu fonksiyonu çağıran devam edebilirsiniz.|  
|`FALSE`|IDE tarafında (örneğin, yetersiz bellek durumunun) ilgili bir sorun oluştu. Eklenti işlem durdurmanız gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İsteğe bağlı olarak ekleyin veya dosya listeden silmek için kaynak denetimi eklentisi isteyen her dosya için tümleştirilmesidir, bu işlevi çağıran `lpFileName`. `fAddRemove` Bayrak listeye eklemek için yeni bir dosya veya silmek için eski bir dosyayı belirtir. `nStatus` Parametre dosyanın durumunu sağlar. Eklenti SCC dosya eklemeye ve silmeye sona erdiğinde arasında döndürür [SccPopulateList](../extensibility/sccpopulatelist-function.md) çağırın.  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` Özelliği bit Visual Studio için gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Dosya durum kodu](../extensibility/file-status-code-enumerator.md)
