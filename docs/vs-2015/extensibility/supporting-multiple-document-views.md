---
title: Çoklu belge görünümlerini destekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9377fc12db8cedba65a418fd32b82a1421bd9b43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160506"
---
# <a name="supporting-multiple-document-views"></a>Birden Çok Belge Görünümünü Destekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyicinizde ayrı belge verileri ve belge görünümü nesneleri oluşturarak bir belgenin birden fazla görünümünü sağlayabilirsiniz. Ek belge görünümü yararlı olabilecek bazı durumlar şunlardır:  
  
- Yeni pencere desteği: düzenleyicide zaten açık bir pencerenin bulunduğu bir kullanıcının **pencere** menüsünde **yeni pencere** komutunu seçerek yeni bir pencere açabildiğinden, Düzenleyicinizde aynı türde iki veya daha fazla görünüm sağlamayı tercih edersiniz.  
  
- Form ve kod görünümü desteği: Düzenleyicinizde farklı türlerin görünümlerini sağlamasını istersiniz. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Örneğin, hem form görünümü hem de kod görünümü sağlar.  
  
  Bunun hakkında daha fazla bilgi için Visual Studio paket şablonu tarafından oluşturulan özel düzenleyici projesindeki EditorFactory.cs dosyasındaki CreateEditorInstance yordamına bakın. Bu proje hakkında daha fazla bilgi için bkz. [Izlenecek yol: özel bir düzenleyici oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Görünümler eşitleniyor  
 Birden çok görünüm uyguladığınızda, tüm görünümlerin verilerle eşitlenmiş şekilde tutulması için belge verileri nesnesi sorumludur. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>Birden çok görünümü verilerle eşleştirmek için üzerinde olay işleme arabirimlerini kullanabilirsiniz.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>Birden çok görünümü eşleştirmek için nesnesini kullanmıyorsanız, belge verileri nesnesinde yapılan değişiklikleri işlemek için kendi olay sisteminizi uygulamanız gerekir. Birden fazla görünümü güncel tutmak için farklı düzeylerde ayrıntı düzeyi kullanabilirsiniz. En yüksek ayrıntı düzeyi ayarıyla, bir görünümü yazarken, diğer görünümler hemen güncellenir. Minimum ayrıntı düzeyi ile diğer görünümler etkinleştirilinceye kadar güncellenmez.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Belge verilerinin zaten açık olup olmadığını belirleme  
 Tümleşik geliştirme ortamındaki (IDE) çalışan belge tablosu (RDT), aşağıdaki diyagramda gösterildiği gibi bir belge için verilerin zaten açık olup olmadığını izlemenize yardımcı olur.  
  
 ![DocDataView grafiği](../extensibility/media/docdataview.gif "DocDataView")  
Birden çok görünüm  
  
 Varsayılan olarak, her görünüm (belge görünümü nesnesi) kendi pencere çerçevesinde ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ) bulunur. Ancak, daha önce belirtildiği gibi, belge verileri birden çok görünümde görüntülenebilir. Bu özelliği etkinleştirmek için, Visual Studio, söz konusu belgenin bir düzenleyicide zaten açık olup olmadığını öğrenmek üzere RDT 'yi denetler. IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Düzenleyici oluşturmak için çağırdığında, parametrede null olmayan bir değer döndürülen bir `punkDocDataExisting` belgenin zaten başka bir düzenleyicide açık olduğunu gösterir. RDT işlevlerinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [çalışma belge tablosu](../extensibility/internals/running-document-table.md).  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Uygulamanızda, `punkDocDataExisting` belge verilerinin düzenleyicinize uygun olup olmadığını öğrenmek için ' de döndürülen belge verileri nesnesini inceleyin. (Örneğin, HTML Düzenleyicisi tarafından yalnızca HTML verileri görüntülenmelidir.) Uygunsa, Düzenleyici fabrikanızın veri için ikinci bir görünüm sağlaması gerekir. `punkDocDataExisting`Parametre değilse `NULL` , belge veri nesnesinin başka bir düzenleyicide açık olması veya daha büyük olasılıkla belge verilerinin, düzenleyiciyle aynı şekilde farklı bir görünümde açık olması mümkündür. Belge verileri, Düzenleyici fabrikanızın desteklemediği farklı bir düzenleyicide açıksa, Visual Studio düzenleyici fabrikanızı açamaz. Daha fazla bilgi için bkz. [nasıl yapılır: belge verilerine görünüm iliştirme](../extensibility/how-to-attach-views-to-document-data.md).
