---
title: SDKReference öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f43c813e688c1e175f1d36e6f06125f92404c48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700173"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference Öğesi (Visual Studio Şablonları)
Öğe şablonunun bir SDK başvurusu kullandığını belirtir.

## <a name="syntax"></a>Syntax

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler
 Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Başvuru](../extensibility/reference-element-visual-studio-templates.md)|Öğe projeye eklendiğinde Eklenecek derleme başvurusunu belirtir.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

## <a name="remarks"></a>Açıklamalar
 Bu metin, öğe şablonu örneği oluşturulduğunda bir projeye eklenecek SDK başvurusunu belirtir.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>Ayrıca bkz.
- [References Öğesi (Visual Studio Şablonları)](../extensibility/references-element-visual-studio-templates.md)
- [Reference Öğesi (Visual Studio Şablonları)](../extensibility/reference-element-visual-studio-templates.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
