---
title: Özellikler penceresi düğmeleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706168"
---
# <a name="properties-window-buttons"></a>Özellikler Penceresi Düğmeleri
Geliştirme diline ve ürün türüne bağlı olarak, **Özellikler** penceresi için araç çubuğunda bazı düğmeler varsayılan olarak görüntülenir. Her durumda, **kategorilere ayrılan**, **sıralama**, **Özellikler**ve **Özellik sayfaları** düğmeleri görüntülenir. Visual C# ve Visual Basic, **Olaylar** düğmesi de görüntülenir. Bazı Visual C++ projelerinde, **vc + + iletileri** ve **vc geçersiz kılmalar** düğmeleri görüntülenir. Diğer proje türleri için ek düğmeler gösterilebilir. **Özellikler** penceresindeki düğmeler hakkında daha fazla bilgi için bkz. [Özellikler penceresi](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Özellikler penceresi düğmelerinin uygulanması
 **Kategorilere ayrılmış** düğmesine tıkladığınızda, Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> nesnenin özelliklerini kategoriye göre sıralamak için odağı olan nesne üzerindeki arabirimini çağırır. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> , `IDispatch` **Özellikler** penceresine sunulan nesnesine uygulanır.

 Negatif değerlere sahip 11 önceden tanımlanmış özellik kategorisi vardır. Özel kategoriler tanımlayabilirsiniz, ancak bunları önceden tanımlanmış kategorilerden ayırt etmek için pozitif değerler atamanızı öneririz.

 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>Yöntemi, belirtilen özellik için uygun özellik kategorisi değerini döndürür. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>Yöntemi, kategori adını içeren bir dize döndürür. Visual Studio standart özellik kategorisi değerlerini bildiğinden, yalnızca özel kategori değerleri için destek sağlamanız gerekir.

 **Alfabetik hale getirme** düğmesine tıkladığınızda Özellikler ada göre alfabetik sırada görüntülenir. Adlar, `IDispatch` yerelleştirilmiş bir sıralama algoritmasına göre alınır.

 **Özellikler** penceresi açık olduğunda, **Özellikler** düğmesi otomatik olarak seçili olarak gösterilir. Ortamın diğer bölümlerinde aynı düğme görüntülenir ve **Özellikler** penceresini göstermek için bu düğmeye tıklayabilirsiniz.

 Seçili nesne için uygulanmıyorken **Özellik sayfaları** düğmesi kullanılamaz `ISpecifyPropertyPages` . Özellik sayfaları, genellikle çözümler ve projelerle ilişkili yapılandırmaya bağımlı özellikleri görüntüler, ancak proje öğeleriyle da ilişkilendirilebilirler (örneğin, Visual C++).

> [!NOTE]
> Yönetilmeyen kod kullanarak **Özellikler** penceresine araç çubuğu düğmeleri ekleyemezsiniz. Bir araç çubuğu düğmesi eklemek için, öğesinden türetilmiş bir yönetilen nesne oluşturmalısınız <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
