---
title: 基本和複雜對應作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: da864b48-6255-4847-9a6f-13e489e8658d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82876310cfa497f8002e7df680281122e90884af
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710309"
---
# <a name="basic-and-complex-mapping-operations"></a>基本和複雜對應作業
BizTalk 對應工具提供各種對應實例的解決方案，範圍從簡單父-子樹狀結構類型作業到涉及迴圈記錄和階層的詳細複雜作業。 對應實例的複雜度是根據您的喜好設定和商務需求；XML 結構描述定義 (XSD) 語言提供相當大的彈性讓您定義結構格式。 幾乎所有對應實例都可分為兩種類別：基本對應和複雜對應。  
  
## <a name="basic-mapping"></a>基本對應  
 基本對應是您可以建立的最常見對應類型。 在基本對應中，輸入和輸出項目都會有一對一的關係。 輸入項目會對應至一個輸出項目，且就只能對應至一個輸出項目。 雖然許多類型的轉換和轉譯是使用基本的對應，例如使用多個 *運算質* 和階層式運算質來處理正在複製的值，基礎實例仍相當地簡單。 基本對應作業同時也包含將來自兩個不同父記錄 (僅發生一次) 的欄位對應至目的結構描述中之單一父記錄下的欄位。  
  
## <a name="complex-mapping"></a>複雜對應  
 複雜對應涉及記錄或欄位的單一執行個體中發生多次 **記錄** 或 **欄位項目** 結構描述樹狀結構中的節點。 這類節點的其 **Max Occurs** 屬性設定值大於一 (1)，表示執行個體訊息中可能有一個以上的對應項目。 當 BizTalk 對應時，使用這種類型的可變計數對應 (也稱為 *迴圈*)，可延伸樣式表語言 (XSL) 樣式表編譯器必須能夠判斷正確的迴圈路徑，要重複執行以產生所需的輸出。  
  
 一般而言，您可以將來源結構描述之迴圈記錄中的欄位連結至目的結構描述之迴圈記錄中的欄位。 輸入執行個體訊息中的對應項目數會決定在輸出執行個體訊息中所建立的項目數。 例如，從範例來源與目的結構描述考量下列 XSD 分割。  
  
### <a name="source-schema-fragment"></a>來源結構描述分割  
  
```  
<xs:element minOccurs="1" maxOccurs="5"  
            name="SrcLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
```  
  
### <a name="destination-schema-fragment"></a>目的結構描述分割  
  
```  
<xs:element minOccurs="0" maxOccurs="unbounded"  
            name="DstLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
```  
  
 在這些分割中：  
  
-   **SrcLoopingRecord**, 、 **記錄** 輸入執行個體訊息中的節點可以發生一到五次。 它也包含子 **欄位項目** 節點 **Field1** （字串） 和 **Field2** （整數），每個執行個體其所有父出現一次。  
  
-   **DstLoopingRecord**, 、 **記錄** 零 (0) 或更多次，可能會發生在輸出執行個體訊息中的節點。 它也包含子 **欄位項目** 節點 **FieldA** （字串） 和 **FieldB** （整數），每個執行個體其所有父出現一次。  
  
 假設 Field1 已對應至 FieldA 而 Field2 已對應至 FieldB，且來自輸入執行個體訊息的下列分割已處理那些對應，則會產生來自輸出執行個體訊息的下列分割。  
  
### <a name="input-instance-message-fragment"></a>輸入執行個體訊息分割  
  
```  
<SrcLoopingRecord>  
    <Field1>A string</Field1>  
    <Field2>10</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>Another string</Field1>  
    <Field2>11</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>A ball of string</Field1>  
    <Field2>12</Field2>  
</SrcLoopingRecord>  
```  
  
### <a name="output-instance-message-fragment"></a>輸出執行個體訊息分割  
  
```  
<DstLoopingRecord>  
    <FieldA>A string</FieldA>  
    <FieldB>10</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
  <FieldA>Another string</FieldA>  
  <FieldB>11</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
    <FieldA>A ball of string</FieldA>  
    <FieldB>12</FieldB>  
</DstLoopingRecord>  
```  
  
 發生次數 **SrcLoopingRecord** 輸入執行個體訊息 (3) 中的元素會決定的次數 **DstLoopingRecord** 輸出執行個體訊息中的項目。  
  
 BizTalk 對應工具不支援使用多個迴圈路徑的對應類型。 這類型的對應涉及將來自來源結構描述中之兩個或更多迴圈記錄的欄位，對應至目的結構描述之單一迴圈記錄內的欄位。 這會有一個問題，就是沒有有效的方式可判斷在輸出執行個體訊息中所產生的項目數目。 多個迴圈路徑會導致出現對應編譯警告，指出目的節點具有多個來源迴圈路徑。 然而，這只是一個警告，並會使用第一個來源迴圈路徑中的重複數目來判斷在輸出執行個體中所產生的項目數目。 您可能需要明確控制迴圈行為使用 **迴圈** 運算質。  
  
 Microsoft BizTalk Server 在引進新類型的迴圈，稱為表格驅動迴圈。 當您的輸出執行個體訊息必須以來自輸入執行個體訊息 (結合一或多個條件約束、來源結構描述的連結或運算質) 的資料為基礎時，表格驅動迴圈就十分有用。 在這類情況下，輸出執行個體訊息可以有多個記錄以輸入執行個體訊息之單一記錄的資料為基礎 (而該輸入執行個體訊息會結合不同條件約束)，或可以有多個記錄以輸入執行個體訊息之多個記錄的資料為基礎。 如需表格驅動迴圈使用**表格迴圈**和**表格抽選程式**運算質，請參閱[表格迴圈和表格擷取程式運算質](../core/table-looping-and-table-extractor-functoids.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)