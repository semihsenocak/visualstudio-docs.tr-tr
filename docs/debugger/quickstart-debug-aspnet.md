---
title: Hata ayıklama ASP.NET Core
description: Visual Studio hata ayıklayıcısını kullanarak ASP.NET Core hata ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bbe3d23301f0853626a930855acf4b595c6a2923
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847882"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Hızlı başlangıç: Visual Studio hata ayıklayıcısı ile ASP.NET Core hata ayıklama

Visual Studio hata ayıklayıcı, uygulamalarınızda hata ayıklamanıza yardımcı olmak için birçok güçlü özellik sunar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **ASP.net**yazın, **Şablonlar**' ı seçin ve sonra **Yeni ASP.NET Core Web uygulaması oluştur**' u seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında **Web**' i seçin ve ardından Ortadaki bölmede **ASP.NET Core Web uygulaması**' nı seçin. **Mydbgapp** gibi bir ad yazın ve **Tamam**' a tıklayın.

    Görüntülenen iletişim kutusunda Ortadaki bölmede **Web uygulaması** ' nı seçin ve ardından **Tamam**' a tıklayın.

    ![Bir Web uygulaması seçin](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    **ASP.NET Core Web uygulaması** proje şablonunu görmüyorsanız **Araçlar**' a gidin  >  ve Visual Studio yükleyicisi açan araçlar**ve Özellikler...**' a gidin. **ASP.net ve Web geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    Visual Studio projeyi oluşturur.

1. Çözüm Gezgini ' de, About.cshtml.cs açın (sayfalar/about. cshtml altında) ve aşağıdaki kodu değiştirin

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    yerine şu kodu yazın:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

*Kesme noktası* , Visual Studio 'nun çalışan kodunuzu askıya alması gerektiğini belirten bir işaretleyicidir, böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz. Hata ayıklamada en temel özelliktir.

1. Kesme noktasını ayarlamak için, işlevin solundaki cilt payın içine tıklayın `doWork` (veya kod satırını seçip **F9**tuşuna basın).

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Kesme noktası açma küme ayracı () solunda ayarlanır `{` .

1. Şimdi **F5** tuşuna basın (veya hata **ayıklamayı başlatmak > hata ayıkla**seçeneğini belirleyin).

1. Web sayfası yüklendiğinde, Web sayfasının en üstündeki **hakkında** bağlantısına tıklayın.

    Hata ayıklayıcı, kesme noktasını ayarladığınız yerde duraklatılır. Hata ayıklayıcının ve uygulama yürütmenin duraklatıldığı ifade sarı oklu belirtilir. İşlev bildiriminden sonra açma ayracı () olan satır `{` `doWork` henüz yürütülmedi.

    ![Kesme noktasına isabet edin](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Bir döngüde veya özyinelemedeki bir kesme noktası varsa veya sık sık adımtığınız çok sayıda kesme noktasına sahipseniz, kodunuzun yalnızca belirli koşullar karşılandığında askıya alındığından emin olmak için [koşullu bir kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) kullanın. Bu, zamandan tasarruf eder ve yeniden oluşturulması zor olan sorunların hatalarını ayıklamanızı da kolaylaştırır.

## <a name="navigate-code"></a>Koda git

Hata ayıklayıcının devam etmesini bildirmek için farklı komutlar vardır. Visual Studio 2017 ' den başlayarak kullanılabilecek yararlı bir kod Gezinti komutu gösteririz.

Kesme noktasında duraklalarken, tıklama `return c2` düğmesine tıklayarak ve ardından tıklama düğmesine tıklayarak **Run to click** deyimin üzerine gelin ![ ](../debugger/media/dbg-tour-run-to-click.png) ve sonra da **Çalıştır** düğmesine basın.

![Tıklama için Çalıştır](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Uygulama yürütmeye devam eder ve düğmeyi tıklattığınız kod satırında duraklar.

Kod içinde ilerlemek için kullanılan yaygın klavye komutları **F10** ve **F11**. Daha ayrıntılı yönergeler için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Bir veri ipucunda değişkenleri İnceleme

1. Geçerli kod satırında (Sarı yürütme işaretçisi tarafından işaretlenir), `c2` bir DataTip göstermek için farenizle nesnenin üzerine gelin.

    ![Veri ipucunu görüntüleme](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Datatıp, değişkenin geçerli değerini gösterir `c2` ve özelliklerini incelemenizi sağlar. Hata ayıklarken, beklemediğinizi bir değer görürseniz, büyük olasılıkla kodun önceki veya çağırma satırlarında bir hata oluşur.

2. Nesnenin geçerli özellik değerlerini görmek için DataTip ' i genişletin `c2` .

3. Kodu yürüttüğünüzde değerini görmeye devam edebilmeniz için veri ipucunu sabitlemek istiyorsanız `c2` , küçük sabitle simgesine tıklayın. (Sabitlenmiş veri ipucunu uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasında kodunuzda test etmek istediğiniz bir değişikliği belirlerseniz, bunu da yapabilirsiniz.

1. `OnGet`Yönteminde ikinci örneğine tıklayın `result.First.Value` ve öğesini `result.First.Value` olarak değiştirin `result.Last.Value` .

1. Hata ayıklayıcıyı ilerletmek ve düzenlenmiş kodu yürütmek için **F10** 'e (veya **hata ayıklama > adımla**) birkaç kez basın.

    ![Düzenle ve devam et](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Düzenle ve devam et")

    **F10** , hata ayıklayıcı bir ifadeyi tek seferde ilerletir, ancak bunlar içine adımlamak yerine işlevler üzerinde adımlar (yine de atladığınız kod).

Düzenle ve devam et ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm sağlamak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
