---
title: "組合器管線元件中的屬性降級 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], properties
- pipeline components, properties
- BizTalk Framework Assembler [pipeline component], properties
- XML Assembler [pipeline component], about XML Assembler
- Flat File Assembler [pipeline component], properties
ms.assetid: c5275638-d594-4b0d-a818-b7a9460b41a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af634d302f01b18c91ebdbb7533673e8b9c545c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="property-demotion-in-assembler-pipeline-components"></a>組合器管線元件中的屬性降級
您可以使用屬性降級將訊息內容中的屬性值複製到訊息內容或其標頭或結尾。 您可以使用在文件或標頭和結尾結構描述中指定的 XPath 運算式來完成屬性降級。  
  
 將日期時間資料從內容屬性寫入產生的文件時，BizTalk Server 會假設所有資料時間資料都是 UTC 格式。  
  
 用來將屬性寫入資料的格式，是由顯示在下表的 XSD 資料型別所決定。  
  
|資料類型|格式|  
|---------------|------------|  
|xs:datetime|yyyy-MM-ddTHH:mm:ss.fffffffZ|  
|xs:date|yyyy-MM-ddZ|  
|xs:gDay|---ddZ|  
|xs:gMonth|--MM—Z|  
|xs:gMonthDay|--MM-ddZ|  
|xs:gYear|yyyyZ|  
|xs:gYearMonth|yyyy-MMZ|  
|xs:time|HH:mm:ss.fffffffZ|  
  
## <a name="property-demotion-and-envelopes"></a>屬性降級和信封  
 在信封中組譯檔案時，將一或多個系統命名空間 — 或您自己的其中一個命名空間 — 中的值降級通常很有用。 一些常見的案例包括：  
  
-   您想要將提交至系統的原始檔案名稱包含在輸出訊息，以讓後端系統能夠追蹤資料的來源。  
  
-   您想將內文訊息中的資料寫入標頭中。 例如，將要命名的出貨寫入下游系統的信封中可能會對於訂單很有用。  
  
-   您想要將多個不同的欄位組合到標頭中，而不要撰寫自訂程式碼。 Xml 組合器或一般檔案組合器中的屬性降級可完成這項工作。  
  
 必須記住，XML 和一般檔案組合器元件兩者都可讓您指定要對信封和文件內容使用的結構描述。 您在選擇用於解譯的相同結構描述，或建立包含不同欄位的新信封結構描述。  
  
 如需這些概念的範例，請參閱[EnvelopeProcessing （BizTalk Server 範例）](../core/envelopeprocessing-biztalk-server-sample.md)。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md)   
 [如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)