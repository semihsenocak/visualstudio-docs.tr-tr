---
title: azurecli-login
description: devinit aracı azurecli-oturum açma.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 74c8144d9442c786bddeae78024fc4cf0d1e0d4a
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006045"
---
# <a name="azurecli-login"></a>azurecli-login

`azurecli-login`Araç, [Azure clı](https://docs.microsoft.com/cli/azure/authenticate-azure-cli?view=azure-cli-latest&preserve-view=true)aracılığıyla Azure Active Directory oturum açmak için kullanılır. Bu araç Azure CLı komutunu kullanır: `az login --use-device-code` , oturum açma işleminin tamamlanabilmesi için konsola yazdırılan yönergeleri izlemeniz gerekir.

## <a name="usage"></a>Kullanım

Her iki özellik de atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                          |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                               |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.     |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `azurecli-login` en son Azure CLI sürümünü yüklemek ve yola eklemektir (yalnızca Windows).

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger az login --use-device-code behavior.",
            "tool": "azurecli-login"
        }
    ]
}
```
