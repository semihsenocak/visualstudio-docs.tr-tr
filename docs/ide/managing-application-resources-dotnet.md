---
title: Uygulama kaynaklarını yönetme (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1815b0efeebf98587fe07384ea0b2c8d1f5e1d90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88992374"
---
# <a name="manage-application-resources-net"></a>Uygulama kaynaklarını yönetme (.NET)

Kaynak dosyaları, bir uygulamanın parçası olan ancak derlenmediği, örneğin simge dosyaları veya ses dosyaları gibi dosyalardır. Bu dosyalar derleme sürecinin bir parçası olmadığından, ikili dosyalarınızı yeniden derlemek zorunda kalmadan bunları değiştirebilirsiniz. Uygulamanızı yerelleştirmek istiyorsanız, uygulamanızı yerelleştirmeniz durumunda değiştirilmesi gereken tüm dizelerin ve diğer kaynakların kaynak dosyalarını kullanmanız gerekir.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [uygulama kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources).

.NET uygulamalarındaki kaynaklar hakkında daha fazla bilgi için bkz. [.net Apps 'Teki kaynaklar](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Kaynaklarla çalışma

Yönetilen bir kod projesinde proje özellikleri penceresini açın. Özellikler penceresini şu şekilde açabilirsiniz:

- **Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **Özellikler** ' i seçin
- **project properties** **CTRL** + **Q** arama kutusuna proje özelliklerini yazma
- Çözüm Gezgini **alt** + **ENTER** seçme **Solution Explorer**

**Kaynaklar** sekmesini seçin. Projenizde bir tane yoksa bir *. resx* dosyası ekleyebilirsiniz, farklı türlerde kaynaklar ekleyip silebilir ve mevcut kaynakları değiştirebilirsiniz.

## <a name="resources-in-other-project-types"></a>Diğer proje türlerindeki kaynaklar

Kaynaklar, .NET projelerinde diğer proje türlerinden farklı şekilde yönetilir. İçindeki kaynaklar hakkında daha fazla bilgi için:

- Evrensel Windows Platformu (UWP) uygulamaları, bkz. [uygulama kaynakları ve kaynak yönetimi sistemi](/windows/uwp/app-resources/)
- C++ projeleri, bkz. [çalışma kaynak dosyaları](/cpp/windows/working-with-resource-files) ve [nasıl yapılır: kaynak oluşturma](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uygulamalarında kaynaklar (.NET Framework)](/dotnet/framework/resources/index)
- [Uygulama kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources)
