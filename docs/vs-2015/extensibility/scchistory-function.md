---
title: SccHistory Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8df85c03201e46768c43fb64cc41b7fa081eb91a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64789794"
---
# <a name="scchistory-function"></a>SccHistory İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, belirtilen dosyaların geçmişini görüntüler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvContext`  
 'ndaki Kaynak denetimi eklentisi bağlam yapısı.  
  
 `hWnd`  
 'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.  
  
 `nFiles`  
 'ndaki Dizide belirtilen dosya sayısı `lpFileName` .  
  
 `lpFileName`  
 'ndaki Dosyaların tam nitelikli adlarını dizisi.  
  
 `fOptions`  
 'ndaki Komut bayrakları (Şu anda kullanılmıyor).  
  
 `pvOptions`  
 'ndaki Kaynak denetimi eklentisi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Sürüm geçmişi başarıyla alındı.|  
|SCC_I_RELOADFILE|Kaynak denetim sistemi, geçmişi getirilirken (örneğin, eski bir sürümünü alarak) diskteki dosyayı gerçekten değiştirdi, bu nedenle IDE 'nin bu dosyayı yeniden yüklemesi gerekir.|  
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|  
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemiyor.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|  
|SCC_E_PROJNOTOPEN|Proje açılmadı.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata. Dosya Geçmişi alınamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak denetimi eklentisi, üst pencere olarak kullanarak her bir dosyanın geçmişini göstermek için kendi iletişim kutusunu görüntüleyebilir `hWnd` . Alternatif olarak, eğer destekleniyorsa, [SccOpenProject](../extensibility/sccopenproject-function.md) için sağlanan isteğe bağlı metin çıkış geri çağırma işlevi kullanılabilir.  
  
 Belirli koşullarda, bu çağrının yürütülmesi sırasında incelenen dosyanın değişebileceğini unutmayın. Örneğin, [!INCLUDE[vsvss](../includes/vsvss-md.md)] Geçmiş komutu kullanıcıya dosyanın eski bir sürümünü elde etmek için bir şans verir. Böyle bir durumda, kaynak denetimi eklentisi, `SCC_I_RELOAD` dosyayı yeniden yüklemek için gereken IDE 'yi uyar ' ı döndürür.  
  
> [!NOTE]
> Kaynak denetimi eklentisi bir dosya dizisi için bu işlevi desteklemiyorsa, yalnızca ilk dosyanın dosya geçmişi görüntülenebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
