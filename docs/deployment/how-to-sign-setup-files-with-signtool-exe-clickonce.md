---
title: Kurulum dosyalarını SignTool.exe ile imzalama (ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 138e84637acb123c445839dc4810547ed8bc2ed3
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809511"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Nasıl yapılır: kurulum dosyalarını SignTool.exe ile Imzalama (ClickOnce)
Bir kurulum programını imzalamak için *SignTool.exe* kullanabilirsiniz (*setup.exe*). Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklü olmamasını sağlamaya yardımcı olur.

 Varsayılan olarak, ClickOnce imzalı bildirimlere ve imzalı bir kurulum programına sahiptir. Ancak, Kurulum programının parametrelerini daha sonra değiştirmek istiyorsanız Kurulum programını daha sonra imzalamanız gerekir. Kurulum programı imzalandıktan sonra parametreleri değiştirirseniz, imza bozulur.

 Aşağıdaki yordam imzasız bildirimler ve imzasız bir kurulum programı oluşturur. Ardından, imzalı bildirimler oluşturmak için Visual Studio 'da ClickOnce imzalama etkinleştirilir. Müşterinin yürütülebilir dosyayı kendi sertifikasıyla imzalayabilmesi için Kurulum programı imzasız olarak kalır.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>İmzasız bir kurulum programı oluşturmak ve daha sonra imzalamak için

1. Geliştirme bilgisayarında, bildirimleri imzalamak istediğiniz sertifikayı yükleyebilirsiniz.

2. **Çözüm Gezgini**içinde projeyi seçin.

3. **Proje** menüsünde, *ProjectName* **özellikleri**' ne tıklayın.

4. **İmzalama** sayfasında, **ClickOnce bildirimlerinin**işaretini kaldırın.

5. **Yayımla** sayfasında, **Önkoşullar**' ı tıklatın.

6. Tüm önkoşulların seçili olduğunu doğrulayın ve ardından **Tamam**' a tıklayın.

7. **Yayımla** sayfasında, yayımlama ayarlarını doğrulayın ve **Şimdi Yayımla**' ya tıklayın.

     Çözüm, imzasız uygulama bildirimini, imzasız dağıtım bildirimini, sürüme özgü dosyaları ve imzasız Kurulum programını yayımlama klasörü konumuna yayımlar.

8. **Yayımla** sayfasında, **Önkoşullar**' ı tıklatın.

9. Önkoşul iletişim **kutusunda,** **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur**seçimini kaldırın.

10. **Yayımla** sayfasında, yayımlama ayarlarını doğrulayın ve **Şimdi Yayımla**' ya tıklayın.

     Çözüm, imzalı uygulama bildirimini, imzalı dağıtım bildirimini ve sürüme özgü dosyaları yayımlama klasörü konumuna yayımlar. İmzasız Kurulum programı, yayımlama işlemi tarafından üzerine yazılmaz.

11. Müşteri sitesinde bir komut istemi açın.

12. *. Exe* dosyasını içeren dizine geçin.

13. *. Exe* dosyasını aşağıdaki komutla imzalayın:

    ```cmd
    signtool sign /sha1 CertificateHash Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

     Örneğin, Kurulum programını imzalamak için aşağıdaki komutlardan birini kullanın:

    ```cmd
    signtool sign /sha1 CCB... Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
