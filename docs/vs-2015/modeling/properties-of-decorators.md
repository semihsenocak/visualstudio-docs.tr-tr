---
title: Dekoratörler özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652012"
---
# <a name="properties-of-decorators"></a>Dekoratörlerin Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dekoratörler, diyagramdaki şekiller veya bağlayıcılar üzerinde görünebilen simgelerle, metin veya genişletme/daraltma köşeli ayraçlardır. Aşağıdaki tablolarda, üç dekoratörün çeşitinin özellikleri gösterilmektedir. Bazı özellikler yalnızca şekil dekoratlarını veya yalnızca bağlayıcı dekoratlarını üzerinde görünür.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Dekoratör Genişlet/Daralt

|Özellik|Açıklama|Varsayılan|
|--------------|-----------------|-------------|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Daraltma dekoratörü Genişlet|
|Name|Dekoratörün adı.|ExpandCollapseDecorator|
|Notlar|Bu dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|SourceTop|

## <a name="icon-decorator"></a>Simge dekoratör

|Özellik|Açıklama|Varsayılan|
|--------------|-----------------|-------------|
|DefaultIcon|Görüntülenecek simgenin veya resim dosyasının yolu.|\<none>|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratör adı.|Simge dekoratör|
|Name|Dekoratörün adı.|Şeklindeki IconDecorator|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Özellik|Açıklama|Varsayılan|
|--------------|-----------------|-------------|
|Ise DefaultText|Görüntülenecek varsayılan metin.|Etiketle|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratör adı.|Etiketle|
|FontSize|Dekoratör içinde görüntülenen metnin yazı tipi boyutu.|8|
|FontStyle|Dekoratör içinde görüntülenen metnin yazı tipi stili.|Düzenli|
|Name|Dekoratörün adı.|Etiketle|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|TargetBottom|

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
