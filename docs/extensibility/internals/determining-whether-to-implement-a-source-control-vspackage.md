---
title: Kaynak denetimi VSPackage ne zaman uygulanır?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16f96191115a509e07b5263f1d10d53ea3b2cc9c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037048"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Kaynak denetimi VSPackage uygulanıp uygulanacağını belirleme

Bu bölüm, kaynak denetimi çözümlerini genişletmek için kaynak denetimi eklentilerinin ve kaynak denetimi VSPackages 'ın seçimlerini elaborates ve uygun bir tümleştirme yolu seçme hakkında geniş yönergeler sağlar.

## <a name="small-source-control-solution-with-limited-resources"></a>Sınırlı kaynaklarla küçük kaynak denetimi çözümü

 Sınırlı kaynaklarınız varsa ve kaynak denetim paketi yazma ek yüküne sahip değilseniz, kaynak denetimi eklentisi API tabanlı eklentiler oluşturabilirsiniz. Bunun yapılması, kaynak denetimi paketleriyle yan yana çalışmanıza olanak sağlar ve isteğe bağlı olarak kaynak denetimi eklentileri ve paketleri arasında geçiş yapabilirsiniz. Daha fazla bilgi için bkz. [kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Zengin özellik kümesine sahip büyük kaynak denetimi çözümü

 Kaynak denetimi eklentisi API 'SI kullanılarak yeterince yakalanmayan zengin kaynak denetimi modeli sağlayan bir kaynak denetimi çözümü uygulamak istiyorsanız, tümleştirme yolu olarak bir kaynak denetim paketi düşünebilirsiniz. Kaynak denetim olaylarını özel bir şekilde işleyebilmeniz için, bu durum özellikle kaynak denetim bağdaştırıcısı paketini (kaynak denetimi eklentileri ile iletişim kuran ve temel bir kaynak denetimi kullanıcı arabirimi sağlar) yerine yenilerini koymak istiyorsanız geçerlidir. Zaten tatmin edici bir kaynak denetimi kullanıcı arabirimine sahipseniz ve bu deneyimi ' de korumak istiyorsanız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , kaynak denetimi paketi seçeneği yalnızca bunu yapmanızı sağlar. Kaynak denetim paketi genel değildir ve yalnızca IDE ile kullanılmak üzere tasarlanmıştır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Kaynak Denetim mantığı ve Kullanıcı arabirimi üzerinde esneklik ve daha zengin denetim sağlayan bir kaynak denetimi çözümü uygulamak istiyorsanız, kaynak denetimi paketi tümleştirme yolunu tercih edebilirsiniz. Seçenekleriniz şunlardır:

1. Kendi kaynak denetimi VSPackage 'ı kaydedin (bkz. [kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Varsayılan kaynak denetimi kullanıcı arabirimini özel Kullanıcı arabiriminiz ile değiştirin (bkz. [Özel Kullanıcı arabirimi](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Kullanılacak glifleri belirtin ve Çözüm Gezgini glif olaylarını işleyin (bkz. [glif denetimi](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Sorgu düzenleme ve sorgu kaydetme olaylarını işle (bkz. sorgu [düzenleme sorgusu kaydetme](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
