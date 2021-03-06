---
title: Araç penceresi kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7b82353247776eb2dac8135a0a412b396d571a1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584722"
---
# <a name="register-a-tool-window"></a>Araç penceresi kaydetme
Araç pencerelerini ve kullanarak kaydedebilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Örnek

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Yukarıdaki kodda, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `PersistedWindowPane` ve `DynamicWindowPane` araç pencerelerini Visual Studio 'ya kaydeder. Kalıcı araç penceresi **Çözüm Gezgini**ve sekmeli bir şekilde yerleşiktir ve dinamik pencereye varsayılan başlangıç konumu ve boyutu verilir. Dinamik pencere, başlangıçta oluşturulmadığını belirten geçici hale getirilir. Bu `DontForceCreate` `ToolWindows` , sistem kayıt defterindeki anahtara bir değer yazar. Daha fazla bilgi için bkz. [araç penceresi görüntü yapılandırması](../vs-2015/extensibility/tool-window-display-configuration.md?view=vs-2015&preserve-view=true).