---
title: Şifreleme Uyarıları
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78923dfd2873b53790421cde3fe01f024e267202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587711"
---
# <a name="cryptography-warnings"></a>Şifreleme Uyarıları
Şifreleme uyarıları, doğru şifreleme kullanımıyla daha güvenli kitaplıkları ve uygulamaları destekler. Bu uyarılar, programınızdaki güvenlik açıklarını önlemeye yardımcı olur. Bu uyarılardan birini devre dışı bırakırsanız, bunun sebebini kodunuzda açıkça işaretlemelisiniz ve ayrıca geliştirme projeniz için güvenlik çalışanını bilgilendirmelisiniz.

|Kural|Description|
|----------|-----------------|
|[CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5350.md)|Zayıf şifreleme algoritmaları ve karma işlevleri bugün çok sayıda nedenden dolayı kullanılır, ancak korudukları verilerin gizliliğini veya bütünlüğünü sağlamak için kullanılmamalıdır.        Bu kural, koddaki TripleDES, SHA1 veya RIPEMD160 algoritmaları bulduğunda tetikler.|
|[CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5351.md)|Bozuk şifreleme algoritmaları güvenli olarak kabul edilmez ve kullanımları kesinlikle önerilmez. Bu kural, MD5 karma algoritmasını veya koddaki DES veya RC2 şifreleme algoritmalarından birini bulduğunda tetikler.|
