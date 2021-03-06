---
title: Uzak Linux bilgisayarlarda Python kodunda hata ayıklama
description: Gerekli yapılandırma adımları, güvenlik ve sorun giderme dahil olmak üzere uzak Linux bilgisayarlarda çalışan Python kodunda hata ayıklamak için Visual Studio 'Yu kullanın.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5307684bde56955f2a4ed77d2ac66b6b30cb1c1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541093"
---
Visual Studio, Windows bilgisayarında Python uygulamalarını yerel olarak ve uzaktan başlatabilir ve hata ayıklayabilir (bkz. [Uzaktan hata ayıklama](../../../debugger/remote-debugging.md)). Ayrıca, hata ayıklayıcı [GPY kitaplığını](https://pypi.org/project/debugpy/)kullanarak, Cpıthon dışında farklı bir işletim sisteminde, cihazda veya Python uygulamasında uzaktan hata ayıklayabilirsiniz.

Hata ayıklayıcı GPY kullanırken, ayıklanmakta olan Python kodu, Visual Studio 'Nun iliştirebileceği hata ayıklama sunucusunu barındırır. Bu barındırma, kodunuzun içeri aktarılması ve etkinleştirilmesi için kodunuzda küçük bir değişiklik yapılmasını gerektirir ve TCP bağlantılarına izin vermek için uzak bilgisayar üzerinde ağ veya güvenlik duvarı yapılandırmalarının gerekli kılabilir.

> [!NOTE]
> Visual Studio 2019 sürüm 16,4 ve önceki sürümlerde [ptvsd kitaplığı](https://pypi.python.org/pypi/ptvsd) kullanıldı. Hata ayıklama GPY kitaplığı, Visual Studio 2019 sürüm 16,5 ' de ptvsd 4 ' ü değiştirdi.

## <a name="set-up-a-linux-computer"></a>Linux bilgisayarı ayarlama

Bu yönergeyi izlemek için aşağıdaki öğeler gereklidir:

- Mac OSX veya Linux gibi bir işletim sisteminde Python çalıştıran uzak bilgisayar.
- Bu bilgisayarın güvenlik duvarında açılan bağlantı noktası 5678 (gelen), uzaktan hata ayıklama için varsayılandır.

> [!NOTE]
> Bu izlenecek yol, Visual Studio 2019 sürüm 16,6 ' i temel alır.

[Azure 'da bir Linux sanal makinesini](/azure/virtual-machines/linux/creation-choices) kolayca oluşturabilir ve Windows 'Dan [Uzak Masaüstü kullanarak erişebilirsiniz](/azure/virtual-machines/linux/use-remote-desktop) . Python varsayılan olarak yüklendiğinden, sanal makine için Ubuntu uygundur; Aksi takdirde, ek Python indirme konumları için [tercih ettiğiniz bir Python yorumlayıcısı yükleme](../../installing-python-interpreters.md) sayfasındaki listeye bakın.

Bir Azure VM için bir güvenlik duvarı kuralı oluşturma hakkında ayrıntılı bilgi için, bkz. [Azure Portal kullanarak Azure 'da BIR VM 'ye bağlantı noktası açma](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Betiği hata ayıklama için hazırla

1. Uzak bilgisayarda, aşağıdaki kodla *Guessing-Game.py* adlı bir Python dosyası oluşturun:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. `debugpy`Paketini kullanarak ortamınıza yükler `pip3 install debugpy` .
   >[!NOTE]
   >Sorun gidermek için ihtiyaç duymanız durumunda yüklü olan, hata ayıklama GPY sürümünü kaydetmek iyi bir fikirdir; hata ayıklama [GPY listesi](https://pypi.org/project/debugpy/) de kullanılabilir sürümleri gösterir.

1. Aşağıdaki kodu, diğer koddan önce *Guessing-Game.py*içindeki olası en erken noktaya ekleyerek uzaktan hata ayıklamayı etkinleştirin. (Katı bir gereksinim olmasa da, işlev çağrılmadan önce oluşturulan herhangi bir arka plan iş parçacığında hata ayıklaması olanaksızdır `listen` .)

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Dosyayı kaydedin ve çalıştırın `python3 guessing-game.py` . ' A çağrı `listen` arka planda çalışır ve diğer bir programla etkileşime geçerek gelen bağlantıları bekler. İsterseniz, işlev, `wait_for_client` `listen` hata ayıklayıcı iliştirene kadar programı engelledikten sonra çağrılabilir.

> [!Tip]
> Ve ' ın yanı sıra, `listen` `wait_for_client` hata ayıklayıcı eklendiğinde bir yardımcı işlevi de sağlar `breakpoint` . Ayrıca, `is_client_connected` hata ayıklayıcısı eklenmişse döndüren bir işlev de vardır `True` (başka işlevler çağrılmadan önce bu sonucu denetlemeniz gerekmez `debugpy` ).

## <a name="attach-remotely-from-python-tools"></a>Python araçlarından uzaktan iliştirme

Bu adımlarda, uzak işlemi durdurmak için basit bir kesme noktası ayarlayacağız.

1. Yerel bilgisayarda Uzak dosyanın bir kopyasını oluşturun ve Visual Studio 'da açın. Dosyanın nerede bulunduğu, ancak adı uzak bilgisayardaki betiğin adıyla eşleşmelidir.

1. Seçim Yerel bilgisayarınızda hata ayıklama GPY için IntelliSense 'i yüklemek üzere, hata ayıklama GPY paketini Python ortamınıza ekleyin.

1. İşleme **Ekle hata ayıkla**öğesini seçin  >  **Attach to Process**.

1. Görüntülenen **Işleme İliştir** Iletişim kutusunda **bağlantı türünü** **Python Remote (hata ayıklama GPY)** olarak ayarlayın.

1. **Bağlantı hedefi** alanına, `tcp://<ip_address>:5678` `<ip_address>` uzak bilgisayarın konumunu (bir açık adres veya myvm.cloudapp.NET gibi bir ad olabilir) ve `:5678` Uzaktan hata ayıklama bağlantı noktası numarası olduğunu girin.

1. Bu bilgisayardaki kullanılabilir hata ayıklama GPY işlemlerinin listesini doldurmak için **ENTER** tuşuna basın:

    ![Bağlantı hedefini girme ve listeleme işlemi](../../media/remote-debugging-attach.png)

    Bu listeyi doldurduktan sonra uzak bilgisayarda başka bir program başlatmanız durumunda **Yenile** düğmesini seçin.

1. Hata ayıklama ve ardından **Ekle**işlemini seçin ya da işleme çift tıklayın.

1. Ardından, komut dosyası uzak bilgisayarda çalışmaya devam ederken, tüm olağan [hata ayıklama](../../debugging-python-in-visual-studio.md) yeteneklerini sunarak, Visual Studio hata ayıklama moduna geçer. Örneğin, satırda bir kesme noktası ayarlayın `if guess < number:` , ardından uzak bilgisayara geçin ve başka bir tahmin girin. Bunu yaptıktan sonra, yerel bilgisayarınızdaki Visual Studio bu kesme noktasında durduktan sonra yerel değişkenleri gösterir ve bu şekilde devam eder:

    ![Kesme noktası isabet edildiğinde Visual Studio hata ayıklamayı duraklatır](../../media/remote-debugging-breakpoint-hit.png)

1. Hata ayıklamayı durdurduğunuzda, Visual Studio, uzak bilgisayarda çalışmaya devam eden programdan ayırır. hata ayıklayıcıları iliştirmeye devam eden GPY, her zaman yeniden eklenebilir.

### <a name="connection-troubleshooting"></a>Bağlantı sorunlarını giderme

1. **Bağlantı türü** için **Python Remote (hata ayıklama GPY)** seçtiğinizden emin olun
1. **Bağlantı hedefi** parolasının uzak koddaki gizli anahtar ile tam olarak eşleştiğinden emin olun.
1. **Bağlantı hedefi** içindeki IP adresinin uzak bilgisayarla eşleşip eşleşmediğini denetleyin.
1. Uzak bilgisayarda uzaktan hata ayıklama bağlantı noktasını açtığınızdan ve bağlantı hedefinde bağlantı noktası sonekini (gibi) dahil edildiğini kontrol edin `:5678` .
    - Farklı bir bağlantı noktası kullanmanız gerekiyorsa, içinde olduğu gibi ' de belirtebilirsiniz `listen` `debugpy.listen((host, port))` . Bu durumda, güvenlik duvarında ilgili bu bağlantı noktasını açın.
1. `pip3 list`Aşağıdaki tabloda, Visual Studio 'da kullandığınız Python araçlarının sürümü tarafından kullanılan eşleştirmelerle döndürülen hata ayıklama için uzak bilgisayarda yüklü olduğunu denetleyin. Gerekirse, uzak bilgisayarda hata ayıklayıcıgpy 'yi güncelleştirin.

    | Visual Studio sürüm | Python araçları/hata ayıklama GPY sürümü |
    | --- | --- |
    | 2019 16,6 | 1.0.0 B5 |
    | 2019 16,5 | 1.0.0 B1 |

> [!NOTE]
> Visual Studio 2019 sürüm 16.0-16.4 kullanılan ptvsd, hata ayıklama GPY değil. Bu sürümler için bu yönergedeki işlem benzerdir, ancak işlev adları farklıdır. Visual Studio 2019 sürüm 16,5, hata ayıklama GPY kullanır, ancak işlev adları ptvsd ile aynı. Yerine `listen` , kullanmanız gerekir `enable_attach` . Yerine `wait_for_client` , kullanmanız gerekir `wait_for_attach` . Yerine `breakpoint` , kullanmanız gerekir `break_into_debugger` .

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Eski hata ayıklama için ptvsd 3. x kullanma
Visual Studio 2017 sürümleri 15,8 ve üzeri, ptvsd sürüm 4.1 + temel alınarak bir hata ayıklayıcı kullanır. Visual Studio 2019 sürümleri 16,5 ve üzeri, hata ayıklama GPY tabanlı bir hata ayıklayıcı kullanır. Hata ayıklayıcının bu sürümleri Python 2,7 ve Python 3.5 + ile uyumludur. Python 2,6, 3,1, 3,4 veya IronPython kullanıyorsanız, Visual Studio hatayı gösterir, hata **ayıklayıcı bu Python ortamını desteklemez**. Aşağıdaki bilgiler yalnızca ptvsd 3. x ile uzaktan hata ayıklama için geçerlidir.

1. Ptvsd 3. x ile, `enable_attach` işlev, çalışan betikle erişimi kısıtlayan ilk bağımsız değişken olarak "gizli" iletmeniz gerekiyordu. Uzaktan hata ayıklayıcıyı eklerken bu gizli anahtarı girersiniz. Önerilmese de, herkesin bağlanmasına izin verebilirsiniz `enable_attach(secret=None)` .

1. Bağlantı hedefi URL 'SI, `tcp://<secret>@<ip_address>:5678` `<secret>` Python kodunda dizenin nerede geçtiğini olduğu yerdir `enable_attach` .

Varsayılan olarak, ptvsd 3. x uzak hata ayıklama sunucusu bağlantısı yalnızca gizli anahtar ile korunur ve tüm veriler düz metin olarak geçirilir. Ptvsd 3. x, daha güvenli bir bağlantı için `tcsp` aşağıdaki şekilde ayarladığınız protokol KULLANıLARAK SSL 'yi destekler:

1. Uzak bilgisayarda, OpenSSL kullanarak otomatik olarak imzalanan ayrı sertifika ve anahtar dosyaları oluşturun:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    İstendiğinde, OpenSSL tarafından istendiğinde **ortak ad** için ana bilgisayar adı veya IP adresini (bağlanmak için kullandığınız) kullanın.

    (Daha fazla bilgi için bkz. Python modülü belgelerinden otomatik olarak [imzalanan sertifikalar](https://docs.python.org/3/library/ssl.html#self-signed-certificates) `ssl` . Bu docs içindeki komutun yalnızca tek bir Birleşik dosya oluşturmadığını unutmayın.)

1. Kodda, `enable_attach` `certfile` `keyfile` dosya adlarını (Bu bağımsız değişkenler standart Python işlevi için aynı anlama sahip olan) ile dahil etme ve bağımsız değişkenler olarak değiştirin `ssl.wrap_socket` :

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Aynı değişikliği yerel bilgisayardaki kod dosyasında da yapabilirsiniz, ancak bu kod gerçekten çalıştırılmadığından, kesinlikle gerekli değildir.

1. Uzak bilgisayarda Python programını yeniden başlatarak hata ayıklama için hazırlayın.

1. Visual Studio ile Windows bilgisayarındaki güvenilen kök CA 'ya sertifika ekleyerek kanalı güvenli hale getirin:

    1. Sertifika dosyasını uzak bilgisayardan yerel bilgisayara kopyalayın.
    1. **Denetim Masası 'nı** açın ve **Yönetimsel Araçlar**  >  **bilgisayar sertifikalarını Yönet**' e gidin.
    1. Görüntülenen pencerede, sol taraftaki **Güvenilen kök sertifika yetkilileri** ' ni genişletin, **Sertifikalar**' a sağ tıklayın ve **Tüm görevler**  >  **içeri aktar**' ı seçin.
    1. ' A gidin ve uzak bilgisayardan kopyalanmış *. cer* dosyasını seçin ve ardından içeri aktarma işlemini gerçekleştirmek için iletişim kutularına tıklayın.

1. Artık `tcps://` **bağlantı hedefi** (veya **niteleyicisi**) protokolü olarak kullanarak, daha önce açıklandığı gibi, Visual Studio 'da iliştirme işlemini yineleyin.

    ![SSL ile uzaktan hata ayıklama aktarımını seçme](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio, SSL üzerinden bağlanırken olası sertifika sorunlarını ister. Uyarıları yoksayabilirsiniz ve devam edebilirsiniz, ancak kanal gizlice dinlede hala şifreleniyor olsa da, ortadaki adam saldırıları için açılabilir.

    1. Aşağıdaki **uzak sertifikaya güvenilir** bir uyarı görürseniz, sertifikayı GÜVENILIR kök CA 'ya doğru bir şekilde eklemediniz demektir. Bu adımları denetleyip yeniden deneyin.

        ![SSL sertifikası güvenilir uyarısı](../../media/remote-debugging-ssl-warning.png)

    1. **Uzak sertifika adının aşağıdaki ana bilgisayar adı uyarısı ile eşleşmiyorsa** , sertifikayı oluştururken **ortak ad** olarak uygun ana bilgisayar adını veya IP adresini kullanmadınız anlamına gelir.

        ![SSL sertifikası konak adı uyarısı](../../media/remote-debugging-ssl-warning2.png)
