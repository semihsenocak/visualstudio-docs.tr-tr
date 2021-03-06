---
title: 'CA2136: Üyeler çakışan saydamlık ek açıklamalarını içermemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3a17a0db7dd4ad1c57d23104a313a78cd1289ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547699"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bu kural, bir tür üyesi <xref:System.Security> üyenin kapsayıcısının güvenlik özniteliğiyle farklı bir saydamlığa sahip bir güvenlik özniteliğiyle işaretlendiğinde ateşlenir.

## <a name="rule-description"></a>Kural Tanımı
 Saydamlık nitelikleri, geniş kapsam kodlu öğelerden daha küçük kapsamlı öğelere uygulanır. Geniş kapsamı ile kod öğelerinin saydamlık öznitelikleri ilk öğeden kapsayan kod öğelerinin saydam öznitelikleri önceliklidir. Örneğin, özniteliğiyle işaretlenmiş bir sınıf, <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlenmiş bir yöntemi içeremez <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu ihlalin giderilmesi için, alt kapsamına sahip kod öğesinden güvenlik özniteliğini kaldırın veya özniteliğini kapsayan kod öğesiyle aynı olacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan gelen uyarıları göstermez.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir yöntemi <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretlenir ve özniteliği ile işaretlenmiş bir sınıfın üyesidir <xref:System.Security.SecurityCriticalAttribute> . Güvenlik güvenli özniteliği kaldırılmalıdır.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
