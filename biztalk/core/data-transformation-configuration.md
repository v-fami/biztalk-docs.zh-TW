---
title: 資料轉換組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XSLT
- maps, compiling
- Source Links property
- BizTalk Mapper, compiler directives
- code samples, XSLT
- compiler directives, copy text and subcontentent value
- compiler directives, copy text value
- maps, XSLT
- compiler directives, copy name
- compiler directives
- maps, code sample [XSLT]
- XSLT, code samples
ms.assetid: 05abe091-5202-4590-99ec-e60ca53a4324
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8304d43f59f63e474a3257915521d5dc36c38d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238958"
---
# <a name="data-transformation-configuration"></a>資料轉換組態
從項目進行對應時，典型的可延伸樣式表語言轉換 (XSLT) 看起來如下。  
  
```  
<xsl:attribute name='CatalogPurposeCode'>  
     <xsl:value-of select='BCT/BCT01/text()'/>  
</xsl:attribute>  
```  
  
 如果項目**BCT01**包含混合的內容，text （） 的使用讓您能夠存取第一個文字只到時間點的第一個子項目，如果有的話。 若在此 XSLT 陳述式中未使用 text()，則結果會造成所有文字內容，加上任何子項目的文字內容，對應為一個文字字串。 設定**來源連結**屬性的連結，可讓您控制複製到目的結構描述所定義之結構的資料來源。  
  
 當您在顯示的格線頁中選取的連結時，其中一個屬性顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗是**來源連結**屬性。 您可以為對應中的每個連結選擇以下可能的值：  
  
-   **複製文字值。** 此為預設值。您可以使用此值以複製輸入執行個體訊息中的項目值或屬性值。 例如，若相關項目為 BoldExample，如下所示：  
  
    ```  
    <BoldExample>This is a <B>Bold Text</B> example.</BoldExample>  
    ```  
  
     複製到輸出執行個體訊息中相關項目或屬性的值為 "This is a"。 對於此類混合內容項目而言，此結果可能並非預期。 但因為混合內容項目是相當罕見，**複製文字值**設定**來源連結**屬性應該是最適合在大部分情況下。  
  
-   **複製名稱。** 使用此值以複製輸入執行個體訊息中的節點名稱。 例如在**複製文字值**描述結果可以是"BoldExample"，這是實際的項目名稱。  
  
-   **複製文字與子內容值。** 使用此值以串連輸入執行個體訊息中的節點值與其所有子節點值。 例如在**複製文字值**說明，結果會是這粗體文字範例。 」，這很可能是定義為包含混合的內容項目的適當的結果。  
  
## <a name="see-also"></a>另請參閱  
 [大量複製運算質](../core/mass-copy-functoid.md)   
 [如何設定來源連結編譯器值](../core/how-to-set-the-source-links-compiler-value.md)   
 [節點階層層級比對](../core/node-hierarchy-level-matching.md)