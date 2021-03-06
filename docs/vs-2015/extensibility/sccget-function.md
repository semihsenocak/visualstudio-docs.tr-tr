---
title: SccGet Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a5d5065ca427f0319174aa59e6b87d356816d4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64803709"
---
# <a name="sccget-function"></a>SccGet İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, görüntüleme ve derleme için bir veya daha fazla dosyanın kopyasını alır, ancak düzenlenmiyor. Çoğu sistemde dosyalar salt okunurdur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 'ndaki Kaynak denetimi eklentisinin bağlam yapısı.  
  
 lendiği  
 'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.  
  
 Nkarşıya  
 'ndaki Dizide belirtilen dosya sayısı `lpFileNames` .  
  
 lpDosyaAdı  
 'ndaki Alınacak dosyaların tam nitelikli adları dizisi.  
  
 fOptions  
 'ndaki Komut bayrakları ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).  
  
 pvOptions  
 'ndaki Kaynak denetimi eklentisi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Get işleminin başarısı.|  
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|  
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemiyor.|  
|SCC_E_FILEISCHECKEDOUT|Kullanıcının şu anda kullanıma aldığı dosya alınamıyor.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|  
|SCC_E_NOSPECIFIEDVERSION|Geçersiz bir sürüm veya tarih/saat belirtildi.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata; dosya eşitlenmedi.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirme yetkisi yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev bir sayı ve alınacak dosyaların bir adı dizisiyle çağrılır. IDE bayrağı geçirirse `SCC_GET_ALL` Bu, içindeki öğelerin `lpFileNames` Dosya, ancak dizinler olmadığı ve belirtilen dizinlerdeki kaynak denetimi altındaki tüm dosyaların alınacağı anlamına gelir.  
  
 `SCC_GET_ALL`Bayrak, `SCC_GET_RECURSIVE` verilen dizinlerin ve tüm alt dizinlerin yanı sıra tüm dosyaları almak için bayrağıyla birleştirilebilir.  
  
> [!NOTE]
> `SCC_GET_RECURSIVE` olmadan hiçbir şekilde geçirilmemelidir `SCC_GET_ALL` . Ayrıca, C:\A ve C:\A\B dizinlerinin her ikisi de özyinelemeli Get, C:\A\B ve tüm alt dizinleriyle iki kez alınacağını unutmayın. Bu, gibi yinelenen nesnelerin dizinin dışında tutulduğundan emin olmak için, IDE 'nin sorumluluğudur (kaynak denetimi eklentisinin değil).  
  
 Son olarak, bir kaynak denetimi eklentisi `SCC_CAP_GET_NOUI` başlatma üzerinde bayrağı belirtse bile, bir get komutu için bir kullanıcı arabirimine sahip olmadığını belirten, bu işlev hala IDE tarafından dosyaları almak için çağrılabilir. Bayrak, IDE 'nin bir get menü öğesini görüntülememesinin ve eklentinin herhangi bir kullanıcı arabirimi sağlaması beklenmediği anlamına gelir.  
  
## <a name="renaming-and-sccget"></a>Yeniden adlandırma ve SccGet  
 Durum: bir Kullanıcı bir dosyayı (örneğin, a.txt) denetler ve değiştirir. a.txt önce iade etmeden önce, ikinci bir Kullanıcı kaynak denetimi veritabanında b.txt a.txt yeniden adlandırır, b.txt denetler, dosyada bazı değişiklikler yapar ve içindeki dosyayı denetler. İlk Kullanıcı ikinci Kullanıcı tarafından yapılan değişiklikleri istemektedir, bu nedenle ilk Kullanıcı a.txt dosyasının yerel sürümlerini b.txt olarak yeniden adlandırarak dosya üzerinde bir get yapar. Ancak, sürüm numaralarını izleyen yerel önbellek, a.txt ilk sürümünün yerel olarak depolanmasını hala önler ve kaynak denetimi farklılıkları çözemez.  
  
 Kaynak denetim sürümlerinin yerel önbelleğinin kaynak denetimi veritabanıyla eşitlenmemiş olması durumunda bu durumu çözmek için iki yol vardır:  
  
1. Kaynak denetim veritabanında Şu anda kullanıma alınmış bir dosyanın yeniden adlandırılmasına izin vermeyin.  
  
2. "Eskileri Sil" öğesinin ve ardından "Yeni Ekle" sözcüğünün eşdeğerini yapın. Aşağıdaki algoritma bunu gerçekleştirmenin bir yoludur.  
  
    1. Kaynak denetim veritabanında b.txt a.txt yeniden adlandırmayla ilgili bilgi edinmek için [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlevini çağırın.  
  
    2. Yerel a.txt b.txt olarak yeniden adlandırın.  
  
    3. `SccGet`Hem a.txt hem de b.txt için işlevi çağırın.  
  
    4. Kaynak denetim veritabanında a.txt bulunmadığından, yerel sürüm önbelleği eksik a.txt sürüm bilgileri temizlenir.  
  
    5. Kullanıma alınan b.txt dosyası, yerel b.txt dosyasının içeriğiyle birleştirilir.  
  
    6. Güncelleştirilmiş b.txt dosyası artık iade edilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
