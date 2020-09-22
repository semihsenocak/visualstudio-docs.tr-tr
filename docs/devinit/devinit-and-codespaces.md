---
title: devinit ve GitHub Codespaces
description: Devinit kullanarak Visual Studio için bir codespace özelleştirmeyi öğrenin.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b42ce84bcb2a336e37d0ffafb2bab6c2dba9ba9d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852211"
---
# <a name="devinit-and-github-codespaces"></a>devinit ve GitHub Codespaces

devinit, [GitHub codespace](https://github.com/features/codespaces) 'e harika bir fikir ve devinit, katkıda bulunanlar oluşturmak, çalıştırmak ve hata ayıklamak için hemen bir kod alanı kurulumu sağlamak üzere kullanılabilir.

GitHub Codespaces ile tümleştirilmesi için, `devinit` `postCreateCommand` `.devcontainer.json` Depo köküne yerleştirilmiş bir dosyada tanımlanan öğesinden çağrılmalıdır. İçindeki dize (ler), `postCreateCommand` Depo codespace 'e kopyalandıktan sonra varsayılan kabukta yürütülür. `postCreateCommand`GitHub Codespaces [Özelleştirme belgelerindeki](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)hakkında daha fazla bilgi edinebilirsiniz. Komutu eklemek için `devinit` `devinit init` `postCreateCommand` Aşağıdaki örneklerde gösterildiği gibi öğesine ekleyebilirsiniz.

Codespace 'e bağlandıktan `devinit init -f <path to .devinit.json>` sonra Visual Studio tümleşik terminalden da çalıştırabilirsiniz.

## <a name="examples"></a>Örnekler

### <a name="with-a-devinitjson-file"></a>.devinit.jsdosya ile
Bu örnekte, aşağıdaki dosyadaki _.devcontainer.js_ , _.devinit.json_ dosyası ile birlikte depo köküne yerleştirilir. Dosyalar bir _. devcontainer_ dizinine de yerleştirilebilecek.

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>As komutları
Bu örnekte _.devcontainer.js_ aşağıdaki dosya depo köküne yerleştirildi ve `devinit run` bir aracı çalıştırmak için programlı olarak çağırılır  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Terminal isteminden

Geçerli çalışma dizini bir _.devinit.js_ dosya içerdiğinde.

```batch
> devinit init
```

_.devinit.js_ , başka bir dizinde olduğunda.

```batch
> devinit init -f path/to/.devinit.json
```