---
title: If etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659066"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı
<xref:System.Activities.Statements.If>Etkinlik bir koşulu değerlendirir ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik, programlama için bir yordamsal modelleme stili kullanırken faydalıdır. <xref:System.Activities.Statements.If>Etkinlik, örneğin bir etkinliğin veya etkinliğin içinde iç içe olabilir <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Parallel> . Bir <xref:System.Activities.Statements.Flowchart> etkinlik kullanıyorsanız <xref:System.Activities.Statements.FlowDecision> bunun yerine bir etkinlik kullanmayı düşünün.

## <a name="if-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.If> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Hangi alt etkinliğin çalıştırılacağını belirleyen koşul. Ayarlamak için, <xref:System.Activities.Statements.If.Condition%2A> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] **IF** Etkinlik tasarımcısında veya özellik kılavuzunda **koşul** kutusuna bir ifade yazın.|
|<xref:System.Activities.Statements.If.Else%2A>|Yanlış|False ise yürütülecek etkinlik <xref:System.Activities.Statements.If.Condition%2A> . **false** Dal tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Else%2A> , **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya bırak" Ipucu metni ile **IF** Etkinlik tasarımcısında **Else** kutusuna bırakın.|
|<xref:System.Activities.Statements.If.Then%2A>|Yanlış|True ise yürütülecek etkinlik <xref:System.Activities.Statements.If.Condition%2A> . **true** Dal tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Then%2A> , **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya **Then** bırak" ipucu metni ile **IF** Etkinlik tasarımcısında bulunan kutuya bırakın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Sıralı](../workflow-designer/sequence-activity-designer.md) [paralel](../workflow-designer/parallel-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)