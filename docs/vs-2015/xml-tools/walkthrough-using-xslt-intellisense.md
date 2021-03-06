---
title: 'İzlenecek yol: XSLT IntelliSense kullanımı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b65f2279270be0d5baef16d6d06e35a7fb0b854
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669535"
---
# <a name="walkthrough-using-xslt-intellisense"></a>İzlenecek Yol: XSLT IntelliSense Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bazı özniteliklerin değerlerini otomatik olarak tamamlamak için XSLT IntelliSense 'in nasıl kullanılacağını gösterir.

### <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>IntelliSense 'i xsl: WITH-param ve xsl: call-template öğeleri ad özniteliğinde kullanmak için

1. Yeni bir XSLT dosyası oluşturun ve aşağıdaki kodu kopyalayın:

    ```
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. Sonra imlecinizi yerleştirip `<xsl:template name="msg23" match="msg23">` ENTER tuşuna basın. Ardından aşağıdaki öğeyi yazmaya başlayın `xsl:call-template` :

    ```
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Şablon adları listesi, `name=""` `xsl:call-template` sizin yazarken öğesinin özniteliğinde görüntülenir.

3. Sonra imlecinizi yerleştirip `<xsl:call-template name="localized-message">` ENTER tuşuna basın. Ardından aşağıdaki öğeyi yazmaya başlayın `xsl:with-param` :

    ```
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Parametre adlarının listesi, `name=""` öğesinin özniteliğinde görüntülenir `xsl:with-param` .

### <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Bir xsl: apply-templates öğesinin mode özniteliğinde IntelliSense kullanmak için

1. Yeni bir XSLT dosyası oluşturun ve aşağıdaki kodu kopyalayın:

    ```
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Sonra imlecinizi yerleştirip `<xsl:apply-templates select="phone" />` ENTER tuşuna basın. Ardından aşağıdaki öğeyi yazmaya başlayın `xsl: apply-templates` :

    ```
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Şablon modlarının listesi, `mode=""` öğesinin özniteliğinde görüntülenir `xsl:apply-templates` .

### <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>IntelliSense 'in stil sayfası-önek ve sonuç-önek öznitelikleri içinde bir xsl: Namespace-Alias öğesi

1. Yeni bir XSLT dosyası oluşturun ve aşağıdaki kodu kopyalayın:

    ```
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Sonra imlecinizi yerleştirip `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` ENTER tuşuna basın. Ardından aşağıdaki öğeyi yazmaya başlayın `xsl:namespace-alias` :

    ```
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Ön eklerin listesinin `stylesheet-prefix` öğesi ve özniteliklerinde görüntülendiğine dikkat edin `result-prefix` `xsl:namespace-alias` .

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi IntelliSense Özellikleri](../xml-tools/xml-editor-intellisense-features.md)
