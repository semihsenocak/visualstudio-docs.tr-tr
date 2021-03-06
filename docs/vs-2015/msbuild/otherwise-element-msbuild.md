---
title: Otherwise öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acf285c895e5160e850b6bc8f20f920279a5e26c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154787"
---
# <a name="otherwise-element-msbuild"></a>Otherwise Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca tüm öğelerin koşulları değerlendirmesi durumunda yürütülecek kod bloğunu belirtir `When` `false` .  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>Syntax  
  
```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Seçin:](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> , Çalıştırılacak kodun bir bölümünü seçmek için alt öğeleri değerlendirir. Öğesinde sıfır veya daha fazla `Choose` öğe olabilir `Otherwise` .|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı [öğe](../msbuild/item-element-msbuild.md) öğeleri kümesi içerir. Öğesinde sıfır veya daha fazla `ItemGroup` öğe olabilir `Otherwise` .|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı [özellik](../msbuild/property-element-msbuild.md) öğeleri kümesi içerir. Öğesinde sıfır veya daha fazla `PropertyGroup` öğe olabilir `Otherwise` .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Seçin:](../msbuild/choose-element-msbuild.md)|, Çalıştırılacak kodun bir bölümünü seçmek için alt öğeleri değerlendirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesinde yalnızca bir öğe olabilir `Otherwise` `Choose` ve en son öğe olmalıdır.  
  
 `Choose`, `When` , Ve `Otherwise` öğeleri bir dizi olası alternatifden daha fazla yürütmek üzere kodun bir bölümünü seçmek için bir yol sağlamak üzere birlikte kullanılır. Daha fazla bilgi için bkz. [koşullu yapılar](../msbuild/msbuild-conditional-constructs.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki proje, `Choose` öğesini ayarlanacak öğelerde hangi özellik değerleri kümesini belirlemek için öğesini kullanır `When` . `Condition`Her iki öğenin öznitelikleri `When` olarak değerlendirilir `false` , öğesindeki özellik değerleri `Otherwise` ayarlanır.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
        </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
