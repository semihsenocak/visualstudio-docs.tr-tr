---
title: IntelliTrace ile olayları görüntüleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffbe0b8365948dc5a69edca390f308cb55ba5a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62929389"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Visual Studio Enterprise IntelliTrace ile olayları görüntüleme (C#, Visual Basic)

IntelliTrace kullanarak belirli olaylar veya olay kategorileri hakkında bilgi toplamak veya olaylara ek olarak tek tek işlev çağrıları hakkında bilgi toplamak için kullanabilirsiniz. Aşağıdaki yordamlarda bunun nasıl yapılacağı gösterilmektedir.

Visual Studio Enterprise sürümünde IntelliTrace kullanabilirsiniz, ancak Professional veya Community sürümlerinde kullanamazsınız.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> IntelliTrace 'i yapılandırma

Yalnızca IntelliTrace olayları ile hata ayıklamayı deneyebilirsiniz. IntelliTrace olayları hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve diğer sistem olaylardır. Hata ayıklamaya başlamadan önce IntelliTrace 'in kaydettiği olayları denetlemek için belirli olayları açmanız veya kapatmanız gerekir. Daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).

- Dosya erişimi için IntelliTrace olayını açın. **Araçlar > seçenekler > ıntellitrace > IntelliTrace olayları** sayfasına gidin ve **Dosya** kategorisini genişletin. **Dosya** olay kategorisini denetleyin. Bu, tüm dosya olaylarının (erişim, kapatma, silme) denetlenmesini sağlar.

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. Bir C# konsol uygulaması oluşturun. Program.cs dosyasında aşağıdaki `using` ifadeyi ekleyin:

    ```csharp
    using System.IO;
    ```

2. Ana yöntemde bir oluşturun, <xref:System.IO.FileStream> buradan okuyun, kapatın ve dosyayı silin. Yalnızca bir kesme noktası ayarlamak için bir yer eklemek üzere başka bir satır ekleyin:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Üzerinde bir kesme noktası ayarlayın `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Hata ayıklamayı Başlat ve IntelliTrace olaylarını görüntüle

1. Hata ayıklamayı her zamanki gibi başlatın. ( **F5** tuşuna basın veya hata **ayıklamayı başlatmak > hata ayıkla**seçeneğine tıklayın.)

    > [!TIP]
    > Bu Windows 'daki değerleri görmek ve kaydetmek için, hata ayıklama sırasında **Yereller** ve **oto** pencerelerini açık tutun.

2. Yürütme kesme noktasında durmaktadır. **Tanılama araçları** penceresini görmüyorsanız, **Windows > IntelliTrace olayları > hata ayıkla**' ya tıklayın.

    **Tanılama araçları** penceresinde **Olaylar** sekmesini bulun (3 sekme, **olay**, **bellek kullanımı**ve **CPU kullanımı**görmeniz gerekir). **Olaylar** sekmesi, hata ayıklayıcının yürütmeden önce son olayla biten kronolojik bir olay listesini gösterir. **Erişim WordSearchInputs.txt**adlı bir olay görmeniz gerekir.

    Aşağıdaki ekran görüntüsü, Visual Studio 2015 güncelleştirme 1 ' dir.

    ![IntelliTrace&#45;güncelleştirme 1](../debugger/media/intellitrace-update1.png "IntelliTrace-güncelleştirme 1")

3. Ayrıntılarını genişletmek için olayı seçin.

    Aşağıdaki ekran görüntüsü, Visual Studio 2015 güncelleştirme 1 ' dir.

    ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")

    Dosya yolu bağlantısını seçerek dosyayı açabilirsiniz. Tam yol adı kullanılabilir değilse, **Dosya Aç** iletişim kutusu görüntülenir.

    Hata **ayıklamayı etkinleştir**' e tıklayarak hata ayıklayıcının bağlamını seçili olayın toplandığı zamana ayarlar, **çağrı yığınında**geçmiş verileri, **Yereller** ve diğer katılan hata ayıklayıcı pencerelerini gösterir. Kaynak kodu kullanılabiliyorsa, Visual Studio bunu incelemenize olanak sağlamak için işaretçiyi kaynak penceresinde karşılık gelen koda taşıdır.

    Aşağıdaki ekran görüntüsü, Visual Studio 2015 güncelleştirme 1 ' dir.

    ![HistoricalDebugging&#45;güncelleştirme 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-güncelleştirme 1")

4. Hatayı bulamazsanız, hataya en önde gelen diğer olayları incelemeyi deneyin. Ayrıca, işlev çağrıları arasında ilerlemek için IntelliTrace kayıt çağrı bilgilerine sahip olabilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar

Geçmiş hata ayıklama ile IntelliTrace 'in gelişmiş özelliklerinden bazılarını kullanabilirsiniz:

- Anlık görüntüleri görüntülemek için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md)
- Değişkenleri İnceleme ve koda gitme hakkında bilgi edinmek için bkz. [geçmiş hata ayıklama ile uygulamanızı İnceleme](../debugger/historical-debugging-inspect-app.md)
