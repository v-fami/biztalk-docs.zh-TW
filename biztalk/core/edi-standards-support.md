---
title: "EDI 標準支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2ef14c5-5f12-40e2-93d7-59b5c5a0d641
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffb23914964d4fd1c114818d6a616c2d57fae434
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-standards-support"></a>EDI 標準支援
[!INCLUDE[prague](../includes/prague-md.md)]提供四種編碼標準的設計和執行階段支援。 下表列出這些編碼標準和詳細資訊的連結。  
  
|編碼標準|產業區塊|參考|  
|-----------------------|----------------------|----------------|  
|UN/EDIFACT|一般產業|[標準網站](http://go.microsoft.com/fwlink/?LinkId=77532)（裝載的參考）<br /><br /> [編碼規則](http://go.microsoft.com/fwlink/?LinkId=77534)iso 9735-4.1|  
|X12|一般產業|[標準網站](http://go.microsoft.com/fwlink/?LinkID=28673)<br /><br /> [規格開發](http://go.microsoft.com/fwlink/?LinkId=77535)|  
|EANCOM|零售|[標準網站](http://go.microsoft.com/fwlink/?LinkId=92861)|  
|HIPAA X12N|健康照護|[HIPAA 實作指南](http://go.microsoft.com/fwlink/?LinkId=77541)<br /><br /> [HIPAA 規格](http://go.microsoft.com/fwlink/?LinkId=77542)|  
  
> [!NOTE]
>  EANCOM 結構描述是 EDIFACT 的子集。 EANCOM 遵循 EDIFACT 所遵循的相同編碼規則。  
  
> [!NOTE]
>  KEDIFACT 是獨立標準，但是幾乎以 EDIFACT 標準為基礎。  
  
## <a name="x12-and-edifact"></a>X12 和 EDIFACT  
 ANSI X12 和 UN/EDIFACT 這兩項標準構成超過 90% 的所有全球交換 EDI 訊息：  
  
-   UN/EDIFACT EDI 國際訊息標準 (用於行政、商業、貿易的 EDI) 是由「聯合國歐洲經濟委員會」(UN/ECE) 所開發並持續維護， 也稱為 EDIFACT。  
  
-   X12 EDI U.S. 訊息標準是由「美國國家標準局」(ANSI) 授權的 Accredited Standards Committee (ASC) X12 委員會所開發並持續維護。  
  
 EDIFACT 大致根據美國X12 標準。 這兩項 EDI 標準在結構上非常類似， 差異包括：  
  
-   這兩項標準的結構化元素名稱不同。 例如，交換控制標頭在 X12 中是 ISA 資料元素，而在 EDIFACT 中是 UNB 資料元素。  
  
-   儘管這兩項標準的許多交易集相對應，但這兩項標準的交易集名稱不同。 例如，訂單在 X12 中是 850 交易集，而在 EDIFACT 中是 ORDERS 交易集。  
  
-   EDIFACT 有選擇性的標頭區段 UNA，可設定結構化元素例如分隔符號和小數點標記，而覆寫管線中定義的預設值。  
  
-   X12 有兩個通知 (名為 TA1 的技術通知和名為 997 的功能通知)，而 EDIFACT 有一個名為 CONTRL 的綜合性通知。  
  
-   X12 建議使用 ASCII 編碼，而 EDIFACT 建議使用 UTF8 編碼。  
  
 [!INCLUDE[prague](../includes/prague-md.md)]支援 KEDIFACT (韓文 EDIFACT) 標準。 KEDIFACT 遵循「UN/EDIFACT 的訊息實作指南」，因此大部分是以 EDIFACT 為基礎。 不過，KEDIFACT 和 X12/EDIFACT 之間還是有差異。 KEDIFACT 使用數個 KEDIFACT 特有的 EDI 結構描述並使用 KECA 字碼頁。  
  
## <a name="hipaa"></a>HIPAA  
 [!INCLUDE[prague](../includes/prague-md.md)]支援 X12 處理，以及因為 HIPAA 處理是 X12 處理，[!INCLUDE[prague](../includes/prague-md.md)]支援 HIPAA 處理。 您會看到提及 X12 支援此文件中，它也適用於 HIPAA 處理。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供額外的 HIPAA 特有支援：  
  
-   一組版本 4010A1 HIPAA 文件結構描述。 如需有關 EDI 和 HIPAA 文件結構描述中[!INCLUDE[prague](../includes/prague-md.md)]，請參閱[EDI 文件結構描述](../core/edi-document-schemas.md)。  
  
-   版本 5010 HIPAA 文件結構描述集合。 如需詳細資訊，請參閱[HIPAA 文件結構描述版本 5010](../core/hipaa-document-schema-version-5010.md)。  
  
-   HIPAA 子文件分割。 如需詳細資訊，請參閱[分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)。  
  
-   支援的 WEDI SNIP 測試前兩個層級： X12 語法完整性和需求[HIPAA 實作指南](http://go.microsoft.com/fwlink/?LinkId=77541)。  
  
 [!INCLUDE[prague](../includes/prague-md.md)]提供了 HIPAA 支援原生 BizTalk Server EDI 功能的一部分。 如需詳細資訊，請參閱[BizTalk Server 中的 EDI 支援](../core/edi-support-in-biztalk-server2.md)。  
  
## <a name="eancom"></a>EANCOM  
 [!INCLUDE[prague](../includes/prague-md.md)]支援 EDIFACT 處理，以及自 EANCOM 處理是 EDIFACT 處理，衍生[!INCLUDE[prague](../includes/prague-md.md)]也支援 EANCOM 處理。 當本文件提及 EDIFACT 支援時，此支援也適用於 EANCOM 處理。  
  
 [!INCLUDE[prague](../includes/prague-md.md)]提供額外的 EANCOM 特有支援：  
  
-   一組版本 EAN94、EAN97 和 EAN02 EANCOM 文件結構描述。 如需有關 EDI 和 EANCOM 文件結構描述中[!INCLUDE[prague](../includes/prague-md.md)]，請參閱[EDI 文件結構描述](../core/edi-document-schemas.md)。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息結構](../core/edi-message-structure.md)   
 [EDI 文件結構描述](../core/edi-document-schemas.md)