---
title: Commands öğesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739691"
---
# <a name="commands-element"></a>Commands öğesi
VSPackage araç çubuğundaki komutların koleksiyonunu temsil eder. Koleksiyonda en fazla beş alt dizi olabilir: menüler, gruplar, düğmeler, comboler ve bit eşlemler.

 Her alt bölüm alt öğesi, örneğin,, \<Menu> BIR GUID ve sayısal tanımlayıcı çifti olan benzersiz bir komut kimliğiyle tanımlanır. GUID, "komut kümesini" tanımlar ve mantıksal olarak ilişkili komutları gruplandırmak için kullanılır. VSPackage, diğer VSPackages tarafından tanımlanan komut kimlikleriyle çakışmaları önlemek için kendi komut kümesini tanımlamalıdır.

## <a name="syntax"></a>Syntax

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|leyebilir|Komutları sağlayan VSPackage 'ı tanımlayan bir GUID.<br /><br /> Örneğin, Package = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|
|[Groups öğesi](../extensibility/groups-element.md)|Bir VSPackage içindeki komut gruplarını tanımlayan girişleri içerir.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Düğme öğelerini gruplandırır.|
|[Bit eşlemler öğesi](../extensibility/bitmaps-element.md)|Bit eşlem öğelerini gruplandırır.|
|[Combos öğesi](../extensibility/combos-element.md)|Grupları açılan öğeleri.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın IDE 'ye sağladığı komutları temsil eden tüm öğeleri tanımlar. Olası öğeler menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutularıdır.|

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir [Commands öğesinin](../extensibility/commands-element.md)nasıl kullanılacağını gösterir.

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
