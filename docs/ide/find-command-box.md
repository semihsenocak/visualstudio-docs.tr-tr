---
title: Find-komut kutusu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591534"
---
# <a name="findcommand-box"></a>Bul/Komut kutusu

**Bul/komut** kutusundan metin araması yapabilir ve Visual Studio komutlarını çalıştırabilirsiniz. **Bul/komut** kutusu hala bir araç çubuğu denetimi olarak kullanılabilir, ancak artık varsayılan olarak görünmez. **Standart** araç çubuğunda **Düğme Ekle veya Kaldır** ' ı ve ardından **bul**' u seçerek **Bul/komut** kutusunu görüntüleyebilirsiniz.

Bir komutu çalıştırmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , () işaretiyle daha büyük bir işareti ile ön yüzü **>** .

**Bul/komut** kutusu, girilen son 20 öğeyi korur ve bir açılan listede görüntüler. **Ok tuşlarını**seçerek listede gezinebilirsiniz.

![&#47;komut kutusu bul](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Metin arama

Varsayılan olarak, **Bul/komut** kutusunda metin belirttiğinizde ve ardından **ENTER** tuşunu seçtiğinizde, Visual Studio geçerli belgeyi veya araç penceresini **dosyalarda bul** iletişim kutusunda belirtilen seçenekleri kullanarak arar. Daha fazla bilgi için bkz. [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Komutları girme

Metin aramak yerine tek bir komut veya diğer ad vermek üzere **Bul/komut** kutusunu kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , komutu daha büyük () simgesiyle bir daha önyüz yapın **>** . Örneğin:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatif olarak, **komut** penceresini tek veya birden çok komut girmek ve yürütmek için de kullanabilirsiniz. Bazı komutlar veya diğer adlar kendileri tarafından girilebilir ve çalıştırılabilir; Diğerlerinin sözdiziminde bağımsız değişkenler olması gerekir. Bağımsız değişkenlere sahip komutların listesi için bkz. [Visual Studio komutları](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Kaçış karakterleri

Komutta bir şapka işareti ( **^** ) karakteri, bir denetim karakteri yerine, bundan hemen sonra gelen karakterin bir şekilde yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerindeki düz tırnak işaretlerini (**"**), boşlukları, baştaki eğik çizgileri, yüzleri veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin:

```
>Edit.Find ^^t /regex
```

Bir giriş işareti, tırnak işaretlerinin içinde mi yoksa dışında mı olduğunu görür. Şapka, satırdaki son karakter ise yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../ide/reference/command-window.md)
- [Metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)
