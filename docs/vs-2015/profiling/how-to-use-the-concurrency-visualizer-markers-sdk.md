---
title: "Nasıl yapılır: eşzamanlılık görselleştiricisi Işaretleyicileri SDK 'sını kullanma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3df1139f34c17055703b1ffcbbe2711d5750b9a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68870042"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Nasıl Yapılır: Eşzamanlılık Görselleştiricisi İşaretçileri SDK'yı Kullanma

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, yayılma ve yazma bayrakları, iletiler ve uyarılar oluşturmak için Eşzamanlılık Görselleştiricisi SDK 'sının nasıl kullanılacağı gösterilmektedir.

### <a name="to-use-c"></a>C++ kullanmak için

1. Uygulamanıza Eşzamanlılık Görselleştiricisi SDK 'Sı desteği ekleyin. Daha fazla bilgi için bkz. [eşzamanlılık GÖRSELLEŞTIRICISI SDK](../profiling/concurrency-visualizer-sdk.md).

2. `include`SDK için bir ifade ve bir `using` ifade ekleyin.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Varsayılan işaretleyici serisinde üç yayılma alanı oluşturmak için kod ekleyin ve her bir yayılma alanına bir bayrak, ileti ve uyarı yazın. Bayrakları, iletileri ve uyarıları yazma yöntemleri [marker_series](../profiling/marker-series-class.md) sınıfının üyeleridir. [Span](../profiling/span-class.md) sınıfı için Oluşturucu bir `marker_series` nesne gerektirir, böylece her yayılma belirli bir işaretleyici serisiyle ilişkilendirilir. `span`Silinen bir sona erer.

    ```cpp
    marker_series series;
    span *flagSpan = new span(series, 1, _T("flag span"));
    series.write_flag(_T("Here is the flag."));
    delete flagSpan;

    span *messageSpan = new span(series, 2, _T("message span"));
    series.write_flag(_T("Here is the message."));
    delete messageSpan;

    span *alertSpan = new span(series, 3, _T("alert span"));
    series.write_flag(_T("Here is the alert."));
    delete alertSpan;
    ```

4. Uygulamayı çalıştırmak için menü çubuğunda **Çözümle**, **Eşzamanlılık görselleştiricisi**, **geçerli projeden başla** ' yı seçin ve eşzamanlılık görselleştiricisi ' ı görüntüleyin. Aşağıdaki çizimde eşzamanlılık görselleştiricisi içindeki üç yayılma ve üç işaret gösterilmektedir.

     ![3 işaretçileri ve uyarılarla eşzamanlılık görselleştiricisi](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. `marker_series`İşaretleyici serisi için bir dize adı alan oluşturucuyu çağırarak ek, özel işaret serisi oluşturmak için kod ekleyin.

    ```cpp
    marker_series flagSeries(_T("flag series"));
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));
    flagSeries.write_flag(1, _T("flag"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete flagSeriesSpan;

    marker_series messageSeries(_T("message series"));
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));
    messageSeries.write_message(1, _T("message"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete messageSeriesSpan;
    ```

6. Eşzamanlılık Görselleştiricisini göstermek için geçerli projeyi başlatın. İki işaretleyici serisi, Iş parçacıkları görünümündeki kendi kulvarları içinde görüntülenir. Aşağıdaki çizimde, iki yeni yayılma gösterilmektedir.

     ![3 özel işaret serisiyle eşzamanlılık görselleştiricisi](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Visual Basic veya C 'yi kullanmak için\#

1. Uygulamanıza Eşzamanlılık Görselleştiricisi SDK 'Sı desteği ekleyin. Daha fazla bilgi için bkz. [eşzamanlılık GÖRSELLEŞTIRICISI SDK](../profiling/concurrency-visualizer-sdk.md).

2. `using` `Imports` SDK için bir veya ifadesini ekleyin.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Varsayılan işaretleyici serisinde üç yayılma alanı oluşturmak için kod ekleyin ve her bir yayılma için bir bayrak, ileti ve uyarı yazın. Statik yöntemi çağırarak bir [span](/previous-versions/hh694189(v=vs.140)) nesnesi oluşturun `EnterSpan` . Varsayılan seriye yazmak için, [işaretleyiciler](/previous-versions/hh694099(v=vs.140)) sınıfının statik yazma yöntemlerini kullanırsınız.

    ```vb
    Dim flagSpan As Span = Markers.EnterSpan("flag span")
    Markers.WriteFlag("Here is the flag.")
    flagSpan.Leave()

    Dim messageSpan As Span = Markers.EnterSpan("message span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteMessage("Here is a message")
    messageSpan.Leave()

    Dim alertSpan As Span = Markers.EnterSpan("alert span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteAlert("Here is an alert")
    alertSpan.Leave()
    ```

    ```csharp
    Span flagSpan = Markers.EnterSpan("flag span");
    Markers.WriteFlag("Here is the flag.");
    flagSpan.Leave();

    Span messageSpan = Markers.EnterSpan("message span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteMessage("Here is a message");
    messageSpan.Leave();

    Span alertSpan = Markers.EnterSpan("alert span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteAlert("Here is an alert");
    alertSpan.Leave();
    ```

4. Uygulamayı çalıştırmak için menü çubuğunda **Çözümle**, **Eşzamanlılık görselleştiricisi**, **geçerli projeden başla** ' yı seçin ve eşzamanlılık görselleştiricisi ' ı görüntüleyin. Aşağıdaki çizimde eşzamanlılık görselleştiricinin Iş parçacığı görünümündeki üç yayılma ve üç işaret gösterilmektedir.

     ![İşaretleyiciler ve uyarılarla eşzamanlılık görselleştiricisi](../profiling/media/cvmarkersmanaged.png "Cvmarkersyönetiliyor")

5. Statik [CreateMarkerSeries](/previous-versions/hh694171(v=vs.140)) yöntemini kullanarak müşteri işaretleyici serisi oluşturmak için kod ekleyin. [MarkerSeries](/previous-versions/hh694127(v=vs.140)) sınıfı, yayılma ve yazma bayrakları, iletiler ve uyarılar oluşturmak için yöntemler içerir.

    ```vb
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")
    System.Threading.Thread.Sleep(1)
    flagSeries.WriteFlag(1, "flag")
    System.Threading.Thread.Sleep(1)
    flagSeriesSpan.Leave()

    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")
    messageSeries.WriteMessage("message")
    System.Threading.Thread.Sleep(1)
    messageSeriesSpan.Leave()
    ```

    ```csharp
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");
    System.Threading.Thread.Sleep(1);
    flagSeries.WriteFlag(1, "flag");
    System.Threading.Thread.Sleep(1);
    flagSeriesSpan.Leave();

    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");
    messageSeries.WriteMessage("message");
    System.Threading.Thread.Sleep(1);
    messageSeriesSpan.Leave();
    ```

6. Eşzamanlılık Görselleştiricisini göstermek için geçerli projeyi başlatın. Üç markör serisi, Iş parçacıkları görünümündeki kendi kulvarları içinde görüntülenir. Aşağıdaki çizimde üç yeni yayılma gösterilmektedir.

     ![3 özel işaret serisiyle eşzamanlılık görselleştiricisi](../profiling/media/cvmarkerseriesmanaged.png "Cvmarkerseriesyönetiliyor")

## <a name="see-also"></a>Ayrıca Bkz.

- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)
