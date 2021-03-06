---
title: 'DA0013: yüksek dize. Split veya String. SUBSTRING kullanımı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159200"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0013 |  
| Kategori |. NET Framework Kullanım Kılavuzu |  
| Profil oluşturma yöntemleri | Örnekleme |  
| İleti | String. Split ve String. SUBSTRING işlevlerinin kullanımını azaltmayı göz önünde bulundurun. |  
| Kural türü | Uyarı |  
  
## <a name="cause"></a>Nedeni  
 System. String. Split veya System. String. Substring yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir bölümüdür. Bir dizedeki alt dizenin varlığını test ediyorsanız System. String. IndexOf veya System. String. IndexOfAny kullanmayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Split yöntemi bir dize nesnesi üzerinde çalışır ve özgün dizenin alt dizelerini içeren yeni bir dize dizisi döndürür. İşlevi döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir dize nesnesi ayırır. Benzer şekilde, substr Yöntemi bir String nesnesi üzerinde çalışır ve istenen alt dizeden eşdeğer olan yeni bir dize döndürür.  
  
 Uygulamanızda bellek ayırmaları yönetimi önemliyse, String. Split ve String. substr yöntemlerine alternatifleri kullanmayı göz önünde bulundurun. Örneğin, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanabilirsiniz.  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 Örnekleme profili verilerinin [Işlev ayrıntıları görünümüne](../profiling/function-details-view.md) gitmek için hata Listesi penceresindeki iletiye çift tıklayın. System. String. Split veya System. String. substr yöntemlerinin en sık kullanımını yapan programın bölümlerini bulmak için çağırma işlevlerini inceleyin. Mümkünse, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanın.
