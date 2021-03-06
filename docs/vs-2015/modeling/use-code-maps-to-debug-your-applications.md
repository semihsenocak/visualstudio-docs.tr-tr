---
title: Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanın | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 33f8d583c369ae365b8d7063a7b0c1d6353a3c56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659473"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod haritaları, büyük kod tabanlarında, bilmediğiniz kodda veya eski kodda kaybolmadığınız önlemenize yardımcı olabilir. Örneğin, hata ayıklama işlemi yaparken birçok dosya ve proje arasında koda bakmanız gerekebilir. Kod parçalarının etrafında gezinmek ve aralarındaki ilişkileri anlamak için kod eşlemelerini kullanın. Bu şekilde, bu kodu başınızdan izlemenize veya ayrı bir diyagram çizmenize gerek kalmaz. Bu nedenle, çalışmanız kesintiye uğradığında, kod haritaları üzerinde çalıştığınız kodla ilgili belleğinizin yenilenmesine yardımcı olur.

 ![Koddaki eşleme ilişkilerini &#45; kod eşleme](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")

 **Bir yeşil ok, imlecinizin düzenleyicide nerede göründüğünü gösterir**

 Kod eşlemeleriyle çalışırken kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

## <a name="understand-the-problem"></a>Sorunu anlama
 Üzerinde çalıştığınız bir çizim programında bir hata olduğunu varsayın. Hatayı yeniden oluşturmak için Visual Studio 'da çözümü açın ve hata ayıklamayı başlatmak için **F5** 'e basın.

 Bir çizgi çizdiğinizde ve **son vuruşumu geri al**' ı seçtiğinizde, bir sonraki satırı çizene kadar hiçbir şey olmaz.

 ![Kod Haritası &#45; yeniden üretme hatası](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")

 Bu nedenle, yöntemi arayarak araştırmaya başlayabilirsiniz `Undo` . Bunu `PaintCanvas` sınıfında bulabilirsiniz.

 ![Kod eşleme &#45; kod bulma](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")

## <a name="start-mapping-the-code"></a>Kodu eşleştirmeyi başlat
 Şimdi `undo` yöntemi ve ilişkilerini eşlemeyi başlatın. Kod düzenleyicisinden, `undo` yöntemini ve başvurduğu alanları yeni bir kod haritasına eklersiniz. Yeni bir eşleme oluşturduğunuzda, kodun dizinini oluşturmak biraz zaman alabilir. Bu, sonraki işlemlerin daha hızlı çalışmasını sağlar.

 ![Kod Haritası &#45; yöntemi ve ilgili alanları göster](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")

> [!TIP]
> Yeşil vurgu eşlemeye eklenen son öğeleri gösterir. Yeşil bir ok, imlecinizin koddaki konumunu gösterir. Öğeler arasındaki oklar farklı ilişkileri temsil eder. Fareyi üzerlerine taşıyarak ve araç ipuçlarını inceleyerek haritadaki öğeler hakkında daha fazla bilgi edinebilirsiniz.

 ![Kod Haritası &#45; araç ipuçlarını gösterme](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")

## <a name="navigate-and-examine-code-from-the-map"></a>Eşlemeden koda gitme ve kodu inceleme
 Her bir alanın kod tanımını görmek için, haritadaki alana çift tıklayın veya alanı seçip **F12**tuşuna basın. Yeşil ok eşlemedeki öğeler arasında hareket eder. Ayrıca kod düzenleyicisindeki imleciniz de otomatik olarak hareket eder.

 ![Kod eşlemesi &#45; alanı tanımını ıncele](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")

 ![Kod eşlemesi &#45; alanı tanımını ıncele](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")

> [!TIP]
> Kod düzenleyicisinde imleci hareket ettirerek yeşil oku eşlemede taşıyabilirsiniz.

## <a name="understand-relationships-between-pieces-of-code"></a>Kod parçaları arasındaki ilişkileri anlama
 Artık hangi diğer kodun ve alanlarıyla etkileşime gireceğini bildirmek istiyorsunuz `history` `paintObjects` . Bu alanlara başvuran tüm yöntemleri eşlemeye ekleyebilirsiniz. Bunu haritadan veya kod düzenleyicisinden yapabilirsiniz.

 ![Kod Haritası &#45; tüm başvuruları bul](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")

 ![Kod düzenleyicisinden bir kod Haritası açın](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")

> [!NOTE]
> Birden çok uygulama genelinde paylaşılan bir projeden (Windows Phone veya Windows Mağazası gibi) öğe eklerseniz, bu öğeler her zaman haritada etkin olan uygulama projesiyle görüntülenir. Bu nedenle, bağlamı başka bir uygulama projesi olarak değiştirirseniz, haritadaki bağlam paylaşılan projeden yeni eklenen öğeler için de değişir. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

 İlişkilerin akışını yeniden düzenlemek ve eşlemenin okunmasını kolaylaştırmak için düzeni değiştirin. Ayrıca, öğeleri sürükleyerek de eşleme etrafında taşıyabilirsiniz.

 ![Kod Haritası &#45; düzeni değiştirme](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")

> [!TIP]
> Varsayılan olarak, **artımlı düzen** açıktır. Yeni öğeler eklediğinizde, bu eşlemeyi mümkün olduğunca az yeniden düzenler. Her yeni öğe eklediğinizde eşlemenin tamamını yeniden düzenlemek için, **artımlı düzeni**kapatın.

 ![Kod Haritası &#45; düzeni değiştirme](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")

 Bu yöntemleri inceleyelim. Haritada **PaintCanvas yöntemine** yöntemine çift tıklayın veya bu yöntemi seçin ve **F12**tuşuna basın. Bu yöntemin boş listeler oluşturduğunu ve bu şekilde olduğunu öğrenirsiniz `history` `paintObjects` .

 ![Kod eşlemesi &#45; yöntemi tanımını Inceleyin](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")

 Şimdi yöntem tanımını incelemek için aynı adımları yineleyin `clear` . `clear`Ve ile bazı görevler gerçekleştireceğini öğrenirsiniz `paintObjects` `history` . Daha sonra yöntemini çağırır `Repaint` .

 ![Kod eşlemesi &#45; yöntemi tanımını Inceleyin](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")

 Şimdi `addPaintObject` yöntem tanımını inceleyin. Ayrıca, ve ile bazı görevler `history` gerçekleştirir `paintObjects` . Ayrıca çağırır `Repaint` .

 ![Kod eşlemesi &#45; yöntemi tanımını Inceleyin](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")

## <a name="find-the-problem-by-examining-the-map"></a>Eşlemeyi inceleyerek sorunu bulma
 Bu, değiştiren ve çağıran tüm yöntemler gibi `history` görünüyor `paintObjects` `Repaint` . Yine de `undo` Yöntem `Repaint` çağrılamasa da `undo` aynı alanları değiştirir. Bu nedenle, ' den arayarak bu sorunu giderebilirsiniz `Repaint` `undo` .

 ![Kod Haritası &#45; eksik yöntem çağrısını bul](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")

 Size bu eksik çağrıyı gösteren bir eşlemeniz yoksa, özellikle de daha karmaşık kod söz konusu olduğunda bu sorunun bulunması daha zor olabilir.

## <a name="share-your-discovery-and-next-steps"></a>Keşfinizi ve sonraki adımları paylaşma
 Siz veya başka biri bu hatayı düzeltmeden önce, eşlemenin üzerine sorunla ve bu sorunun düzeltilmesiyle ilgili notlar ekleyebilirsiniz.

 ![Kod eşlemesi &#45; açıklama ve izleme için öğeleri işaretle](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")

 Örneğin, eşlemeye açıklamalar ekleyebilir ve renkler kullanarak öğeleri işaretleyebilirsiniz.

 ![Kod eşleme &#45; açıklamalı ve bayraklı öğeler](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")

 Microsoft Outlook yüklüyse, eşlemeyi başkalarına e-postayla gönderebilirsiniz. Eşlemeyi bir görüntü veya başka bir biçim olarak dışarı da aktarabilirsiniz.

 ![Kod Haritası &#45; paylaşma, dışarı aktarma, posta](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")

## <a name="fix-the-problem-and-show-what-you-did"></a>Sorunu giderme ve ne yaptığınızı gösterme
 Bu hatayı onarmak için, öğesine çağrısını eklersiniz `Repaint` `undo` .

 ![Kod eşleme &#45; eksik yöntem çağrısı Ekle](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")

 Düzeltmenizi onaylamak için hata ayıklama oturumunu yeniden başlatır ve hatayı yeniden oluşturmaya çalışırsınız. Şimdi **son vuruşumu geri al** ' ın seçilmesi, beklediği gibi çalışarak doğru düzeltmeyi yaptığını onayladınız.

 ![Kod Haritası &#45; kodu düzeltmesini onaylayın](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")

 Eşlemeyi yaptığınız düzeltmeyi gösterecek şekilde güncelleştirebilirsiniz.

 ![Kod eşlemesi, eksik yöntem çağrısıyla güncelleştirme haritasını &#45;](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")

 Haritanız artık **geri alma** ve yeniden **çizmeyi**arasında bir bağlantı gösterir.

 ![Kod eşlemesi &#45; metot çağrısıyla Haritayı güncelleştirmiş](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")

> [!NOTE]
> Eşlemeyi güncelleştirdiğinizde, eşlemeyi oluşturmak için kullanılan kod dizininin güncelleştirdiğini belirten bir ileti görebilirsiniz. Bu, birisinin kodu eşlemenizin geçerli kodla eşleşmemesine neden olacak şekilde değiştirdiği anlamına gelir. Bu sizi eşlemeyi güncelleştirmekten alıkoymaz, ancak kodla eşleştiğini doğrulamak için eşlemeyi yeniden oluşturmak zorunda kalabilirsiniz.

 Artık araştırmanızı bitirdiniz. Kodu eşleştirerek sorunu başarıyla buldunuz ve giderdiniz. Ayrıca kodda gezinmeye ve öğrendiklerinizi hatırlamanıza yardımcı olan ve sorunu gidermek için attığınız adımları gösteren bir eşlemeniz de vardır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama kodu görselleştirirken çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) [Visualize code](../modeling/visualize-code.md)
