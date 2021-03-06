---
title: 'Nasıl yapılır: Alana Özgü Dil Tasarımcısı genişletme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: faac29c59b78d8f3f1a0260b0b7a8ace16169f9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916794"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Nasıl yapılır: Etki Alanına Özgü Dil Tasarımcısını Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir tasarımcıda DSL tanımlarını düzenlemek için kullandığınız uzantılar yapabilirsiniz. Yapabileceğiniz uzantı türleri arasında menü komutları ekleme, sürükle ve çift tıklama hareketleri için işleyiciler ekleme ve belirli değer veya ilişki türleri değiştiğinde tetiklenen kurallar sayılabilir. Uzantılar, Visual Studio Tümleştirme Uzantısı (VSıX) olarak paketlenebilir ve diğer kullanıcılara dağıtılabilir.

## <a name="setting-up-the-solution"></a>Çözümü kurma
 Uzantınızın kodunu içeren bir proje ve projeyi dışarı aktaran bir VSıX projesi ayarlayın. Çözümünüz aynı VSıX 'e dahil edilen diğer projeleri içerebilir.

#### <a name="to-create-a-dsl-designer-extension-solution"></a>DSL Tasarımcısı uzantısı çözümü oluşturmak için

1. Sınıf kitaplığı proje şablonunu kullanarak yeni bir proje oluşturun. **Yeni proje** iletişim kutusunda, **Visual C#** ' ye tıklayın ve ardından orta penceredeki **sınıf kitaplığı**' na tıklayın.

     Bu proje, uzantılarınızın kodunu içerecektir.

2. VSıX proje şablonunu kullanarak yeni bir proje oluşturun. **Yeni proje** iletişim kutusunda, **Visual C#**' ı genişletin, **genişletilebilirlik**' e tıklayın ve ardından ortadaki pencerede **VSIX projesi**' ni seçin.

     **Çözüme Ekle**' yi seçin.

     Kaynak. Extension. valtmanifest VSıX bildirim düzenleyicisinde açılır.

3. Içerik alanının üzerinde **Içerik Ekle**' ye tıklayın.

4. **Içerik Ekle** iletişim kutusunda, **MEF bileşeni**Için **bir içerik türü seçin** ' i ayarlayın ve **projeyi** sınıf kitaplığı projeniz olarak ayarlayın.

5. **Sürümleri Seç** ' e tıklayın ve **Visual Studio Enterprise** işaretli olduğundan emin olun.

6. VSıX projesinin çözümün başlangıç projesi olduğundan emin olun.

7. Sınıf kitaplığı projesinde, aşağıdaki derlemelere başvurular ekleyin:

     Microsoft. VisualStudio. CoreUtility

     Microsoft. VisualStudio. model. SDK. 11.0

     Microsoft. VisualStudio. modellemesi. SDK. diyagramlar. 11.0

     Microsoft. VisualStudio. modellemesi. SDK. DslDefinition. 11.0

     Microsoft. VisualStudio. model. SDK. Integration. 11.0

     System. ComponentModel. Composition

     System. Drawing

     System. Drawing. Design

     System. Windows. Forms

## <a name="testing-and-deployment"></a>Test ve dağıtım
 Bu konudaki herhangi bir uzantıyı test etmek için çözümü derleyin ve çalıştırın. Deneysel bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] açılır. Bu örnekte, bir DSL çözümü açın. DslDefinition diyagramını düzenleyin. Uzantı davranışı görülebilir.

 Uzantıları ana [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve diğer bilgisayarlara dağıtmak için aşağıdaki adımları izleyin:

1. VSIX projenizde VSIX yükleme dosyasını bin \\ * \\ \* . vsix ' de bulun

2. Bu dosyayı hedef bilgisayara kopyalayın ve ardından Windows Gezgini 'nde (veya dosya Gezgini) çift tıklayın.

    Uzantının [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklendiğini doğrulamak için Uzantı Yöneticisi açılır.

   Uzantıyı kaldırmak için şu adımları izleyin:

3. ' nde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , **Araçlar** menüsünde **Uzantı Yöneticisi**' ne tıklayın.

4. Uzantıyı seçin ve silin.

## <a name="adding-a-shortcut-menu-command"></a>Kısayol menü komutu ekleme
 DSL Tasarımcısı yüzeyinde veya DSL Gezgini penceresinde kısayol menü komutu görünmesini sağlamak için, aşağıdaki gibi bir sınıf yazın.

 Sınıfının uygulanması `ICommandExtension` ve özniteliğine sahip olması gerekir `DslDefinitionModelCommandExtension` .

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handling-mouse-gestures"></a>Fare hareketlerini işleme
 Kod, menü komutunun koduna benzer.

```
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="responding-to-value-changes"></a>Değer değişikliklerine yanıt verme
 Bu işleyicinin doğru çalışması için bir etki alanı modelinin olması gerekir. Basit bir etki alanı modeli sağlıyoruz.

```
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

 Aşağıdaki kod basit bir model uygular. Yer tutucuyu değiştirmek için yeni bir GUID oluşturun.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```
