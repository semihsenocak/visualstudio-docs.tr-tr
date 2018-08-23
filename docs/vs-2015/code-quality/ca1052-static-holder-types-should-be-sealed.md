---
title: 'CA1052: Statik tutucu türleri mühürlenmelidir | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3b0cf46a81332b51f5ba749ce44b0116d1d685ef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42675169"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statik tutucu türleri mühürlenmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda en son sürümünü şu yolda bulunabilir: [CA1052: statik tutucu türleri korumalı](https://docs.microsoft.com/visualstudio/code-quality/ca1052-static-holder-types-should-be-sealed).  
  
TypeName | StaticHolderTypesShouldBeSealed |  
| Checkıd | CA1052 |  
| Kategori | Microsoft.Design|  
| Yeni değişiklik | Bozucu |  
  
## <a name="cause"></a>Sebep  
 Ortak veya korumalı tür yalnızca statik üyeleri içerir ve ile bildirilmedi [korumalı](http://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](http://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) değiştiricisi.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu kural türü türetilmiş türde geçersiz kılınabilir herhangi bir işlevsellik sağlamaz çünkü yalnızca statik üyeleri içeren bir tür devralınacak şekilde tasarlanmamıştır olduğunu varsayar. Devralınan düşünülmemiştir bir tür ile işaretlenmelidir `sealed` değiştiricisi, bir taban türü olarak kullanılmasını önlemek için.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Bu kural ihlalini düzeltmek için türü olarak işaretlemek `sealed`. Hedefliyorsanız [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 veya daha önceki türü olarak işaretlemek için iyi bir yaklaşım olup `static`. Bu şekilde, sınıf oluşturulmasını önlemek için bir özel yapıcı bildirmek olmamasına özen gösterin.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Türü yalnızca devralınacak şekilde tasarlanmıştır, bu kuraldan bir uyarıyı gizler. Olmaması `sealed` değiştiricisi önerir türü temel tür olarak kullanışlıdır.  
  
## <a name="example-of-a-violation"></a>Bir ihlali örneği  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kuralını ihlal eden bir tür gösterir.  
  
### <a name="code"></a>Kod  
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]  
  
## <a name="fix-with-the-static-modifier"></a>Statik değiştirici ile düzeltin  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, türü ile işaretleyerek bu kural ihlalini düzeltmek gösterilmektedir `static` değiştiricisi.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]  
  
## <a name="related-rules"></a>İlgili kuralları  
 [CA1053: Statik tutucu türlerinde oluşturucular bulunmamalıdır](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)


