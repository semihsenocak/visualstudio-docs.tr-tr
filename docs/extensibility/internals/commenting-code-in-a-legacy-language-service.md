---
title: Eski dil hizmetindeki kodu açıklama ekleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709433"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Eski dil hizmetindeki yorum kodu
Programlama dilleri genellikle kodun açıklamasına veya açıklamasına açıklama eklemek için bir yol sağlar. Yorum, kod hakkında ek bilgiler sağlayan ancak derleme veya yorum sırasında yoksayılan bir metin bölümüdür.

 Yönetilen paket çerçevesi (MPF) sınıfları, seçilen metnin yorum oluşturma ve açıklama kaldırma desteği sağlar.

## <a name="comment-styles"></a>Açıklama stilleri
İki genel açıklama stili vardır:

1. Açıklamanın tek bir satırda olduğu satır açıklamaları.

2. Açıklamanın birden çok satır içerebilen blok açıklamaları.

Satır açıklamalarının genellikle başlangıç karakteri (veya karakterleri), blok açıklamaları ise başlangıç ve bitiş karakterlerinden oluşmalıdır. Örneğin, C# ' de bir satır yorumu ile başlar `//` ve bir blok yorumu ile başlar `/*` ve ile biter `*/` .

Kullanıcı, **Düzenle**Gelişmiş menüsünden komut **Açıklama seçimini** seçtiğinde  >  **Advanced** , komut, <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> sınıfındaki yöntemine yönlendirilir <xref:Microsoft.VisualStudio.Package.Source> . Kullanıcı **seçimi açıklama**Kaldır komutunu seçtiğinde, komut <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> yöntemine yönlendirilir.

## <a name="support-code-comments"></a>Kod açıklamalarını destekleme
 Dil hizmetinizin, adlandırılmış parametresi aracılığıyla kod açıklamalarını desteklemesini sağlayabilirsiniz `EnableCommenting` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Bu <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> , sınıfının özelliğini ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . Dil hizmeti özelliklerini ayarlama hakkında daha fazla bilgi için bkz. [eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Ayrıca, <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> <xref:Microsoft.VisualStudio.Package.CommentInfo> diliniz için açıklama karakterleriyle bir yapı döndürmek için yöntemini geçersiz kılmanız gerekir. C# stili çizgi Açıklama karakterleri varsayılandır.

### <a name="example"></a>Örnek
 Yöntemin örnek bir uygulamasını aşağıda bulabilirsiniz <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> .

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
- [Eski dil hizmetini Kaydet](../../extensibility/internals/registering-a-legacy-language-service1.md)
