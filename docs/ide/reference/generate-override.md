---
title: Bir yöntemi geçersiz kılma oluştur
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569250"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio 'da bir geçersiz kılma oluştur

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** , Bir temel sınıftan geçersiz kılınabilen her bir yöntem için kodu hemen oluşturmanıza olanak sağlar.

**Ne zaman:** Bir temel sınıf yöntemini geçersiz kılmak ve imzayı otomatik olarak oluşturmak istiyorsunuz.

**Neden:** Yöntem imzasını kendiniz yazabilirsiniz, ancak bu özellik imzayı otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. `override` `Overrides` Bir geçersiz kılma yöntemi eklemek istediğiniz C# ' ta veya Visual Basic, ardından bir boşluk ile yazın.

   - C#:

      ![IntelliSense C 'yi geçersiz kıl #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![IntelliSense VB 'yi geçersiz kıl](media/override-intellisense-vb.png)

2. Temel sınıftan geçersiz kılmak istediğiniz yöntemi seçin.

   > [!TIP]
   > - Özellik simgesini kullanın ![Özellik simgesi](media/override-property-cs.png) Listedeki özellikleri göstermek veya gizlemek için.
   > - Yöntem simgesini kullanın ![Yöntem simgesi](media/override-method-cs.png) listedeki yöntemleri göstermek veya gizlemek için.

   Seçilen yöntem veya özellik, bir geçersiz kılma olarak sınıfa eklenir ve uygulanmasına hazırlanın.

   - C#:

       ![Sonuç C 'yi geçersiz kıl #](media/override-result-cs.png)

   - Visual Basic:

       ![Geçersiz kılma sonucu VB](media/override-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
