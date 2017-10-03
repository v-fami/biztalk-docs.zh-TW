---
title: "HIPAA 結構描述的觸發程序欄位註解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1389284-a2ec-44e7-a2f1-8d26f83fd31d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d3bf6d53ec95ebfc57cff646ce5658fc6b1f4a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hipaa-schema-trigger-field-annotations"></a>HIPAA 結構描述的觸發程序欄位註解
EDI 區段通常包含修飾區段意義的辨識符號。 例如，N1 區段可能包含 “BT” 辨識元素以表示「帳單收件人」，或可能包含 “ST” 辨識元素以表示「出貨收件人」。 通常這些欄位的解讀方式是交由商務邏輯決定，而且解譯器會將 N1 區段的所有執行個體解析成相同的 XML 記錄名稱。不過，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 隨附的 HIPAA 結構描述含有註解，可讓 EDI 解譯器根據存在的辨識元素來建立唯一的 XML 記錄。  
  
 **觸發程序欄位的實作**  
  
 觸發程序欄位會實作為一對描述區段元素的 XML 屬性和造成此記錄可建立的觸發程序值。 下表描述這些屬性：  
  
|Attribute|目的|  
|---------------|-------------|  
|trigger_field|會檢查觸發值區段欄位。|  
|trigger_value|觸發程序的值。<br /><br /> 這可能包含單一值，或以空格分隔的值清單。|  
  
 下表顯示觸發程序註解會顯示在 HIPAA 結構描述、 會導致觸發程序啟動，EDI 區段和產生的 XML 資料之後處理區段。  
  
|結構描述的觸發程序註解|比對 N1 區段|結果產生的 XML 資料|  
|-------------------------------|-------------------------|------------------------|  
|`<xs:element name="TS835W1_1000A_Loop">  <xs:annotation>   <xs:appinfo>    <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayerIdentification_TS835W1_1000A/N101__EntityIdentifierCode"     trigger_value="PR" notes="Payer Identification" />    </xs:appinfo>  </xs:annotation>`|N1 * PR\*Contoso\*1763\*0000000 ~|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|`<xs:element name="TS835W1_1000B_Loop">   <xs:annotation>    <xs:appinfo>     <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayeeIdentification_TS835W1_1000B/N101__EntityIdentifierCode"     trigger_value="PE" notes="Payee Identification" />    </xs:appinfo>   </xs:annotation>`|N1 * PE\*Fabrikam\*FI\*9999999 ~|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
 **觸發程序欄位的 EDI 解譯器處理**  
  
 收到 HIPAA 交易設定，如果 EDI 解譯器遇到含有觸發程序欄位的區段，它會使用觸發程序資訊產生的區段和觸發程序組合特有的 XML 記錄。 比方說，在下列 EDI 資料中，有兩個有不同的值 N101、 PR 和 PE 的 N1 區段：  
  
```  
  
N1*PR*Contoso*XV*0000000~  
N3*N301__PayerAddressLine~  
N4*N401__PayerCityName*N4*N403__PayerPost**N4*N406~  
……  
N1*PE*Fabrikam*FI*9999999~  
N3*N301__PayeeAddressLine~  
N4*N401__PayeeCityName*N4*N403__PayeePost**N4*N406~  
  
```  
  
 當 EDI 解譯器處理，出現在結構描述的觸發程序欄位註解會在兩個不同的 XML 記錄根據 N101，< N1_PayerIdentification_TS835W1_1000A > 的值與 < N1_PayeeIdentification_TS835W1_1000B >，對應至 N1 * PR 和 N1\*PE。  
  
 傳送時，EDI 組合器將會卸除後置字元"_"字元，對於包含觸發程序的註解欄位之後。 比方說，這兩個 < N1_PayerIdentification_TS835W1_1000A > 和 < N1_PayeeIdentification_TS835W1_1000B > 將會同時變成 N1。  
  
 **預設值區段和觸發程序欄位**  
  
 下表包含有關的預設區段和觸發程序欄位用於 HIPAA 文件的一部分提供[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]:  
  
> [!NOTE]
>  與觸發程序欄位搭配使用個別的觸發程序值可能不同結構描述之間。  
  
|觸發程序具有區段。|觸發程序欄位|  
|--------------------------|-------------------|  
|AMT|AMT01|  
|CRC|CRC01|  
|DTM|DTM01|  
|DTP|DTP01|  
|ENT|ENT02|  
|HI|HI01:01|  
|N1|N101|  
|NM1|NM01|  
|NTE|NTE01|  
|REF|REF01|  
|RMR|RMR01|