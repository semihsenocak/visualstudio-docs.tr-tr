---
title: SccDirDiff Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701008"
---
# <a name="sccdirdiff-function"></a>SccDirDiff işlevi
Bu işlev, istemci diskinde geçerli yerel dizin ve kaynak denetimi altındaki karşılık gelen proje arasındaki farkları görüntüler.

## <a name="syntax"></a>Söz dizimi

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpDirName

'ndaki Görsel bir farkı göstermek için yerel dizinin tam yolu.

 dwFlags

'ndaki Komut bayrakları (bkz. açıklamalar bölümü).

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Disk üzerindeki dizin, kaynak kodu denetimindeki projeyle aynıdır.|
|SCC_I_FILESDIFFER|Disk üzerindeki dizin, kaynak kodu denetimindeki projeden farklı.|
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|
|SCC_E_FILENOTCONTROLLED|Dizin, kaynak kodu denetimi altında değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|
|SCC_E_FILENOTEXIST|Yerel dizin bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetimi eklentisinin kullanıcıya belirtilen bir dizin üzerinde yapılan değişikliklerin bir listesini görüntülemesini istemek için kullanılır. Eklenti, kullanıcının disk üzerindeki dizini ile sürüm denetimi altında karşılık gelen proje arasındaki farkları göstermek için kendi penceresini kendi tercih ettiği biçimde açar.

 Bir eklenti dizinlerin karşılaştırılmasını destekliyorsa, "hızlı fark" seçenekleri desteklenmediği halde bir dosya adı temelinde dizinlerin karşılaştırılmasını desteklememelidir.

|`dwFlags`|Yorumlama|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Büyük/küçük harfe duyarsız karşılaştırma (hızlı fark veya görsel için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Boşluğu yoksayar (hızlı fark veya görsel için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Kaynak denetimi eklentisi tarafından destekleniyorsa, dizini, bayt bayt olarak sessizce karşılaştırır.|
|SCC_DIFF_QD_CHECKSUM|Eklenti tarafından destekleniyorsa, dizini bir sağlama toplamı aracılığıyla sessizce karşılaştırır veya desteklenmiyorsa SCC_DIFF_QD_CONTENTS geri döner.|
|SCC_DIFF_QD_TIME|Eklenti tarafından destekleniyorsa, dizini zaman damgası aracılığıyla sessizce karşılaştırır veya desteklenmiyorsa SCC_DIFF_QD_CHECKSUM veya SCC_DIFF_QD_CONTENTS geri döner.|

> [!NOTE]
> Bu işlev, [SccDiff](../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Ancak, bir kaynak denetimi eklentisi dizinler için "hızlı fark" işlemini desteklememe seçeneğini seçebilirler.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
