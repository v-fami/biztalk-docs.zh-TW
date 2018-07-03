---
title: EDI 標準支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2ef14c5-5f12-40e2-93d7-59b5c5a0d641
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb4d85b4972991054914baea2014b6d268a24eb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007127"
---
# <a name="edi-standards-support"></a>EDI 標準支援
BizTalk Server 提供的四個編碼標準的設計和執行階段支援。 下表列出這些編碼標準和詳細資訊的連結。  
  
|編碼標準|產業區塊|參考|  
|-----------------------|----------------------|----------------|  
|UN/EDIFACT|一般產業|[標準網站](http://go.microsoft.com/fwlink/?LinkId=77532)（承載參考）<br /><br /> [編碼規則](http://go.microsoft.com/fwlink/?LinkId=77534)每個 ISO 9735 4.1|  
|X12|一般產業|[標準網站](http://go.microsoft.com/fwlink/?LinkID=28673)<br /><br /> [規格開發](http://go.microsoft.com/fwlink/?LinkId=77535)|  
|EANCOM|零售|[標準網站](http://go.microsoft.com/fwlink/?LinkId=92861)|  
|HIPAA X12N|健康照護|[HIPAA 實作指南](http://go.microsoft.com/fwlink/?LinkId=77541)<br /><br /> [HIPAA 規格](http://go.microsoft.com/fwlink/?LinkId=77542)|  
  
> [!NOTE]
>  EANCOM 結構描述是 EDIFACT 的子集。 EANCOM 遵循 EDIFACT 所遵循的相同編碼規則。  
  
> [!NOTE]
>  KEDIFACT 是獨立標準，但是幾乎以 EDIFACT 標準為基礎。  
  
## <a name="x12-and-edifact"></a>X12 和 EDIFACT  
 ANSI X12 和 UN/EDIFACT 這兩項標準構成超過 90% 的所有全球交換 EDI 訊息：  
  
- UN/EDIFACT EDI 國際訊息標準 (用於行政、商業、貿易的 EDI) 是由「聯合國歐洲經濟委員會」(UN/ECE) 所開發並持續維護， 也稱為 EDIFACT。  
  
- X12 EDI U.S. 訊息標準是由「美國國家標準局」(ANSI) 授權的 Accredited Standards Committee (ASC) X12 委員會所開發並持續維護。  
  
  EDIFACT 很大部分基於美國X12 標準。 這兩項 EDI 標準在結構上非常類似， 差異包括：  
  
- 這兩項標準的結構化元素名稱不同。 例如，交換控制標頭在 X12 中是 ISA 資料元素，而在 EDIFACT 中是 UNB 資料元素。  
  
- 儘管這兩項標準的許多交易集相對應，但這兩項標準的交易集名稱不同。 例如，訂單在 X12 中是 850 交易集，而在 EDIFACT 中是 ORDERS 交易集。  
  
- EDIFACT 有選擇性的標頭區段 UNA，可設定結構化元素例如分隔符號和小數點標記，而覆寫管線中定義的預設值。  
  
- X12 有兩個通知 (名為 TA1 的技術通知和名為 997 的功能通知)，而 EDIFACT 有一個名為 CONTRL 的綜合性通知。  
  
- X12 建議使用 ASCII 編碼，而 EDIFACT 建議使用 UTF8 編碼。  
  
  BizTalk Server 支援 KEDIFACT (韓文 EDIFACT) 標準。 KEDIFACT 遵循「UN/EDIFACT 的訊息實作指南」，因此大部分是以 EDIFACT 為基礎。 不過，KEDIFACT 和 X12/EDIFACT 之間還是有差異。 KEDIFACT 使用數個 KEDIFACT 特有的 EDI 結構描述並使用 KECA 字碼頁。  
  
## <a name="hipaa"></a>HIPAA  
 BizTalk Server 支援 X12 處理，而由於 HIPAA 處理是 x12 處理衍生項目，BizTalk Server 支援 HIPAA 處理。 您看到提及 X12 支援本文中，它也適用於 HIPAA 處理。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供額外的 HIPAA 特有支援：  
  
- 一組版本 4010A1 HIPAA 文件結構描述。 如需有關 BizTalk Server 中的 EDI 和 HIPAA 文件結構描述的詳細資訊，請參閱 < [EDI 文件結構描述](../core/edi-document-schemas.md)。  
  
- 版本 5010 HIPAA 文件結構描述集合。 如需詳細資訊，請參閱 < [HIPAA 文件結構描述版本 5010](../core/hipaa-document-schema-version-5010.md)。  
  
- HIPAA 子文件分割。 如需詳細資訊，請參閱 <<c0> [ 分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)。  
  
- WEDI SNIP 測試前兩個層級的支援： X12 語法完整性和需求[HIPAA 實作指南](http://go.microsoft.com/fwlink/?LinkId=77541)。  
  
  BizTalk Server 提供了 HIPAA 支援的原生的 BizTalk Server EDI 功能的一部分。 如需詳細資訊，請參閱 < [BizTalk Server 中的 EDI 支援](../core/edi-support-in-biztalk-server2.md)。  
  
## <a name="eancom"></a>EANCOM  
 BizTalk Server 支援 EDIFACT 處理，由於 EANCOM 處理衍生的 EDIFACT 處理，BizTalk Server 也支援 EANCOM 處理。 當本文件提及 EDIFACT 支援時，此支援也適用於 EANCOM 處理。  
  
 BizTalk Server 提供額外的 EANCOM 特有支援：  
  
-   一組版本 EAN94、EAN97 和 EAN02 EANCOM 文件結構描述。 如需有關 BizTalk Server 中的 EDI 和 EANCOM 文件結構描述的詳細資訊，請參閱 < [EDI 文件結構描述](../core/edi-document-schemas.md)。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息結構](../core/edi-message-structure.md)   
 [EDI 文件結構描述](../core/edi-document-schemas.md)