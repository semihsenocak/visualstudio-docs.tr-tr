---
title: Visual Studio’yu onarın
titleSuffix: ''
description: Visual Studio 2017 yüklemesini onarmayı öğrenin
ms.date: 06/15/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda72206059e5c14c46d332e44ea0de481004296
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418970"
---
# <a name="repair-visual-studio"></a>Visual Studio’yu onarın

Bazen Visual Studio yüklemenizin hasar görmüş veya bozuk hale gelir. Güncelleştirme, güncelleştirmeleri de dahil olmak üzere tüm yük işlemlerinde karşıya yüklenmeye yönelik sorunları düzeltmek için faydalıdır.

## <a name="when-to-use-repair"></a>Onarma ne zaman kullanılır?
* Yükleme yükü sorunlarınız varsa. Bu durum, dosyayı diske yazarken başarılı olmazsa ve bozuk dosya silinerek düzeltilemeyebilir. Onar, gerekli dosyaları yeniden alabilir. 
* İstemci tarafı karşıdan yükleme sorunlarınız varsa. Herhangi bir bağlantı veya ara sunucu sorununu çözdüğü varsayılarak, onarım yardımcı olabilir. 
* Visual Studio 'Yu güncelleştirirken sorun yaşıyorsanız. Onarma birçok yaygın güncelleştirme sorununu düzeltir. 

> [!TIP] 
> Bu yüklemede, Windows Installer gibi temel bir Windows hizmetindeki bir sorun neden olduysa, onarım aynı soruna karşı daha fazla sürebilir. Systemik sorunları bozuk bir Windows Installer veya kararsız bir internet bağlantısı içerebilir. Bir systemik sorunu denetlemek için, yükleme işleminden oluşturulan hata raporunu kullanın.

> [!NOTE] 
> Visual Studio 'Yu onarma Kullanıcı ayarlarını sıfırlar ve zaten sahip olduğunuz derlemeleri yeniden kurar. Bir ürün sorunu yaşıyorsanız, onarma sorunu çözemediğinden bir [Visual Studio geri bildirim bileti](https://developercommunity.visualstudio.com/content/problem/post.html?space=8)oluşturun.

## <a name="how-to-repair"></a>Onarma
::: moniker range="vs-2017"

1. Bilgisayarınızda **Visual Studio yükleyicisi** bulun.

     Örneğin, Windows 10 yıldönümü güncelleştirmesi veya üzerini çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

   > [!NOTE]
   > Bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi**olarak **"d"** harfi altında listelenmiş olabilir.
   >
   > Alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın, **daha fazla**' yı seçin ve ardından **Onar**' ı seçin.

    ![Visual Studio Yükleyicisi Visual Studio 'Yu onarın](media/repair-visual-studio.png "Visual Studio Yükleyicisi Visual Studio 'Yu onarın")

   > [!NOTE]
   > Visual Studio 'Yu onarmak ortamı sıfırlar. Yükselme, Kullanıcı ayarları ve profiller olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği yalnızca Visual Studio 'nun yüklü örnekleri için görünür. **Onar** seçeneğini görmüyorsanız, Visual Studio yükleyicisi listelenen bir sürümde "yüklü" yerine "kullanılabilir" olarak **daha fazla** seçim yapmış olursunuz.

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda **Visual Studio yükleyicisi** bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

     ![Visual Studio Yükleyicisi açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisi açın")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Onar**' ı seçin.

     ![Visual Studio 2019 'yi onarma](media/vs-2019/vs-installer-repair.png "Visual Studio 2019 'yi onarma")

   > [!NOTE]
   > Visual Studio 'Yu onarmak ortamı sıfırlar. Yükselme, Kullanıcı ayarları ve profiller olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği yalnızca Visual Studio 'nun yüklü örnekleri için görünür. **Onar** seçeneğini görmüyorsanız, Visual Studio yükleyicisi listelenen bir sürümde "yüklü" yerine "kullanılabilir" olarak **daha fazla** seçim yapmış olursunuz.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Visual Studio yükleme ve yükseltme sorunlarını giderme](troubleshooting-installation-issues.md)
