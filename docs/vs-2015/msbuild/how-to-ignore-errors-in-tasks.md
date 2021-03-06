---
title: 'Nasıl yapılır: görevlerdeki hataları yoksayma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5025cc3e9dc0e13c3ae4658d129f5d0ac94f6fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156599"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Nasıl Yapılır: Görevlerdeki Hataları Yoksayma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen bir derlemeyi belirli görevlerde hatalara karşı dayanıklı olmasını isteyebilirsiniz. Kritik olmayan görevler başarısız olursa, gerekli çıktıyı hala üretebileceğinden, derlemeyi devam ettirmek istersiniz. Örneğin, bir proje `SendMail` her bileşen oluşturulduktan sonra e-posta iletisi göndermek için bir görev kullanıyorsa, posta sunucuları kullanılamadığında ve durum iletileri gönderilemediği zaman bile yapılandırmanın tamamlanmasına devam edebilmesi için kabul edilebilir olarak düşünebilirsiniz. Ya da örneğin, derleme sırasında ara dosyalar silinirse, bu dosyalar silinemese bile, derleme tamamlanana kadar devam etmek için kabul edilebilir olarak düşünebilirsiniz.  
  
## <a name="using-the-continueonerror-attribute"></a>Devam eden özniteliğini kullanma  
 `ContinueOnError`Öğesinin özniteliği bir `Task` görev hatası oluştuğunda bir yapılandırmanın durmasını veya devam edip etmediğini denetler. Bu öznitelik, derleme devam ettiğinde hataların hata ya da uyarı olarak değerlendirilip değerlendirilmediğini denetler.  
  
 `ContinueOnError`Özniteliği aşağıdaki değerlerden birini içerebilir:  
  
- **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.  
  
- **Errportadcontinue**. Bir görev başarısız olduğunda, öğedeki sonraki görevler `Target` ve derleme yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.  
  
- **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğe ve yapı içindeki kalan görevler `Target` yürütülmez ve tüm `Target` öğe ve derleme başarısız olarak kabul edilir.  
  
  4,5 ' den önceki .NET Framework sürümleri yalnızca `true` ve değerlerini destekliyordu `false` .  
  
  Varsayılan değeri `ContinueOnError` `ErrorAndStop` . Özniteliğini olarak ayarlarsanız `ErrorAndStop` , davranışı proje dosyasını okuyan herkese açık hale getirebilirsiniz.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Görevdeki bir hatayı yok saymak için  
  
- `ContinueOnError`Görevin özniteliğini kullanın. Örneğin:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `Build` hedefin hala çalıştığını ve bir görev başarısız olsa bile derlemenin başarılı olarak kabul edileceğini gösterir `Delete` .  
  
```  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.
[MSBUILD](msbuild.md)  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
