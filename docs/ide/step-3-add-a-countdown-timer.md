---
title: '3. Adım: Geri sayım zamanlayıcısı ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ca2dce7f6f9ddc484b67f250f34d69747c6e46e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579876"
---
# <a name="step-3-add-a-countdown-timer"></a>3. Adım: Geri sayım zamanlayıcısı ekleme

Bu öğreticinin üçüncü bölümünde, bir geri sayım süreölçeri ekleyerek, test takici 'in tamamlaması için kalan saniye sayısını izleyebilirsiniz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Geri sayım Zamanlayıcısı eklemek için

1. Önceki yordamda yaptığınız gibi, **timeleft**adlı bir tamsayı değişkeni ekleyin. Kodunuzun aşağıdaki gibi görünmesi gerekir.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Artık, belirttiğiniz süre sonunda bir olay harekete geçiren bir zamanlayıcı gibi saniye sayısını sayan bir yönteme ihtiyacınız vardır.

2. Tasarım penceresinde <xref:System.Windows.Forms.Timer> **araç kutusu** **bileşen** kategorisinden bir denetimi formunuza taşıyın.

     Denetim, tasarım penceresinin altındaki gri alanda görüntülenir.

3. Formunda, az önce eklediğiniz **Süreölçer1** simgesini seçin ve **Interval** özelliğini **1000**olarak ayarlayın.

     Aralık değeri milisaniyelik olduğundan, 1000 değeri <xref:System.Windows.Forms.Timer.Tick> olayın her saniye tetiklenmesine neden olur.

4. Formunda **Zamanlayıcı** denetimine çift tıklayın veya seçin ve ardından **ENTER** tuşunu seçin.

     Kod Düzenleyicisi görünür ve az önce eklediğiniz Tick olay işleyicisinin yöntemini görüntüler.

5. Aşağıdaki deyimlerini yeni olay işleyicisi yöntemine ekleyin.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Ne eklediklerinize bağlı olarak Zamanlayıcı, **timeleft** tamsayı değişkeninin 0 ' dan büyük olup olmadığını belirleyerek, zaman aşımına uğrar ve sürenin bitmediğini denetler. Varsa, zaman hala kalır. Süreölçer ilk olarak 1 ' den zaman kaldı ve sonra **timeLabel** denetiminin **Text** özelliğini güncelleştirir ve bu da, kaç saniye kaldığını test eden bir şekilde görüntüler.

     Zaman yoksa, süreölçer yanıt vermez ve **timeLabel** denetiminin metin değişikliğini **zaman** aşımına göre gösterir. Bir ileti kutusu, sınavın daha fazla olduğunu ve yanıtın ortaya çıkarduğunu duyurduğunu ve bu durumda addend1 ve addend2 ekleyerek ortaya çıkarduğunu duyurur. **StartButton** denetiminin **Enabled** özelliği **true** olarak ayarlanır, böylece test takici başka bir test başlatabilir.

     Yeni bir ifade eklediniz `if else` , bu, programları kararlar almak için nasıl söylersiniz. Bir `if else` ifade aşağıdaki gibi görünür.

    > [!NOTE]
    > Aşağıdaki örnek yalnızca tanıtım amaçlıdır; projenize eklemeyin.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     `else`Ek probleme yanıtını göstermek için bloğa eklediğiniz ifadeye yakından bakın.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     İfade, `addend1 + addend2` değerleri iki değişkene birlikte ekler. İlk kısım ( `sum.Value` ), doğru yanıtı göstermek için Sum NumericUpDown denetiminin **Value** özelliğini kullanır. Daha sonra test yanıtlarını denetlemek için aynı özelliği kullanırsınız.

     Test sahipleri, bir denetimi kullanarak daha kolay sayı girebilir <xref:System.Windows.Forms.NumericUpDown> , bu da matematik sorunlarına yanıtlar için bir tane kullanmanızı sağlar. Tüm olası yanıtlar 0 ile 100 arasında tüm sayılardır. **Minimum**, **Maksimum**ve **DecimalPlaces** özelliklerinin varsayılan değerlerini bırakarak, test takipçilerin ondalık sayı, negatif sayı veya çok yüksek sayı girememesini sağlayabilirsiniz. (Test takipçilerin 3,141 girmelerini, ancak 3,1415 değil, izin vermek istiyorsanız, **DecimalPlaces** özelliğini 3 olarak ayarlayabilirsiniz.)

6. Yöntemin sonuna üç satır ekleyin `StartTheQuiz()` , bu nedenle kod aşağıdaki gibi görünür.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Artık, test başladıktan sonra **timeleft** değişkeni 30 olarak ayarlanır ve **timeLabel** denetiminin **Text** özelliği 30 saniyeye ayarlanır. Ardından <xref:System.Windows.Forms.Timer.Start> Zamanlayıcı denetiminin yöntemi geri sayıma başlar. (Test yanıtı henüz denetlemez.)

7. Programınızı kaydedin, çalıştırın ve ardından formdaki **Başlat** düğmesini seçin.

     Süreölçer, sayıyı aşağı doğru olarak başlatır. Zaman çalıştığında, test sonlanır ve yanıt görüntülenir. Aşağıdaki çizimde devam eden bir test gösterilmektedir.

     ![Matematik testi devam ediyor](../ide/media/express_addcountdown.png)<br/>
*Matematik testi devam ediyor*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 4. **[Adım: CheckTheAnswer () metodunu ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)**.

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md).
