---
title: Akış çizelgesi etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a85efea49d641fa54774c1428d15f7d8218ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656701"
---
# <a name="flowchart-activity-designer"></a>Flowchart Etkinlik Tasarımcısı
<xref:System.Activities.Statements.Flowchart>Etkinlik, karmaşık akış denetimlerini tanımlayan ve yöneten iş akışları oluşturmak için kullanılır. Bir <xref:System.Activities.Statements.Flowchart> kod içinde veya kullanılarak yazılabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Bu konu, [!INCLUDE[wfd2](../includes/wfd2-md.md)] deneyimi belgelemektedir. [!INCLUDE[wfd1](../includes/wfd1-md.md)]İş akışı etkinlik Tasarımcısı, geliştiricilerin iş akışlarını doğal bir şekilde yazarmasını sağlar.

## <a name="the-flowchart-activity"></a>Akış çizelgesi etkinliği
 , <xref:System.Activities.Statements.Flowchart> <xref:System.Activities.Statements.Flowchart.StartNode%2A> İş akışı başladığında yürütülen bir benzersiz belirtir ve <xref:System.Activities.Statements.Flowchart.Nodes%2A> rastgele döngüler oluşturmak veya herhangi bir zamanda iş akışındaki herhangi bir yere yürütme akışını yapmak için bağlantılı bir ağı kullanır.

### <a name="using-the-flowchart-activity-designer"></a>Akış çizelgesi etkinlik tasarımcısını kullanma
 **Akış çizelgesi** etkinlik Tasarımcısı, **araç kutusu '** nda, araç **kutusu** sekmesine tıklanarak erişilen (alternatif olarak, **Flowchart** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** veya Ctrl + Alt + X) akış çizelgesi kategorisinde bulunabilir.

 **Akış çizelgesi** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, bir [!INCLUDE[wfd2](../includes/wfd2-md.md)] kök etkinlik olarak ya da başka bir denetim akışı etkinliğinin alt öğesi olarak, etkinlik tasarımcılarının normalde yerleştirildiği yüzey üzerinde bırakılabilir. **Akış çizelgesi** etkinlik Tasarımcısı boş bir yüzey üzerine bırakıldığında [!INCLUDE[wfd2](../includes/wfd2-md.md)] , <xref:System.Activities.Statements.Flowchart> Varsayılan olarak kendisini yürütmeyi Başlatan başlangıç düğümünün yeşil bir top olarak temsil edildiği genişletilmiş bir görünümde sunan bir etkinlik oluşturur. **Akış çizelgesi** etkinlik Tasarımcısı başka bir denetim akışı etkinliğine bırakıldığında, kendisini, **akış çizelgesi** etkinlik tasarımcısına çift tıklayarak genişletilebilen, simge durumuna küçültülmüş bir görünümde sunar. **Araç kutusundaki** herhangi bir etkinlik, diğer denetim akışı etkinlikleri dahil olmak üzere doğrudan **akış çizelgesi** etkinlik tasarımcısına sürüklenebilir.

 Çeşitli etkinlik tasarımcılarını tuvale sürükledikten sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)] <xref:System.Activities.Activity> temsil ettikleri nesneler, yürütme sırasını belirtmek için birbirine bağlanabilir. Kaynak etkinlik ve hedef etkinlik arasında bir bağlantı oluşturmak için, kaynak etkinliği ve kare tutamaçları tasarlayıcı üzerinde fare, onun her tarafında görünür. Kare tutamaçlardan birine tıklayın ve fare düğmesini fareyle üzerine gelindiğinde hedef etkinliğin etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki etkinlik arasında bir bağlantı oluşturulur.

### <a name="flowchart-activity-properties"></a>Akış çizelgesi etkinlik özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Flowchart> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının görünen adını belirtir. Varsayılan değer akış çizelgesi ' dir. Değer, **Özellikler** penceresinde veya doğrudan etkinlik Tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Yanlış|Bunun içinde kapsamı belirlenmiş değişkenlerin koleksiyonu, <xref:System.Activities.Statements.Flowchart> alt etkinlikleri genelinde durum paylaşmalıdır.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Yanlış|<xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.Flowchart> Başlatıldığında yürütülür.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Yanlış|İçindeki nesnelerin koleksiyonunu içerir <xref:System.Activities.Statements.FlowNode> <xref:System.Activities.Statements.Flowchart> .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış çizelgesi](../workflow-designer/flowchart-activity-designers.md) [flowkararı](../workflow-designer/flowdecision-activity-designer.md) [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)