---
title: 'Nasıl yapılır: özel galeri için Atom akışı oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204204"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Nasıl Yapılır: Özel Bir Galeri için Atom Akışı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantıları içeren bir intranet konumuna bir atom (RSS) akışı oluşturabilir ve akışı **uzantılara ve güncelleştirmelere** özel galeri olarak ekleyebilirsiniz. Daha fazla bilgi için bkz. [özel galeriler](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Atom akışı oluşturma  
 Özel Galeri olarak bir Atom akışı oluşturmak için, önce uzantılarınızı (. vsix Files) bir klasöre toplamanız gerekir. İsterseniz bunları alt klasörler halinde düzenleyebilirsiniz. Ayrıca aşağıdaki kaynaklara ihtiyacınız olacaktır:  
  
- Uzantıları özel galeri olarak kullanılabilir hale getiren bir atom.xml dosyası. atom.xml dosyasını **uzantılara ve güncelleştirmelere**bağlama hakkında daha fazla bilgi için bkz. [özel galeriler](../extensibility/private-galleries.md).  
  
- Uzantılardan ayıklanan görüntü dosyalarını içeren bir klasör (örneğin, ekran görüntüleri). atom.xml dosyası, **Uzantılar ve güncelleştirmelerde**kullanılabilmesi için bu görüntülere yönelik göreli bağlantıları içerir.  
  
  Örneğin, aşağıdaki iki uzantıyı bir klasöre topladığınızı varsayalım:  
  
- Boş bir VSıX proje şablonu olan Template_Wizard_239. vsix.  
  
- SelectionHighlight. vsix, seçilen bir kelimenin tüm örneklerini vurgulamak için bir araçtır.  
  
  atom.xml dosyanın içeriği aşağıdaki örneğe benzer:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 İki bağlantı etiketlerinin görüntünün oluşturulan klasöründeki ekran görüntülerini ifade ettiğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Galeriler](../extensibility/private-galleries.md)
