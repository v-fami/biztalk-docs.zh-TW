---
title: "處理接收的通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67f67a95-7368-40c2-a162-6ffc9de076fc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1205c7cec5a013fef89eac49e6b953cf5f752626
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="processing-a-received-acknowledgment"></a>處理接收的通知
如果協議中指定相關屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會預期技術通知。 對於 X12，這是**預期 TA1**屬性**通知**頁面中，單向協議**協議屬性**對話方塊或從後援協議屬性。 對於 EDIFACT，這是**訊息回條 (CONTRL 必須是)**屬性**通知**頁面中，單向協議**協議屬性**對話方塊方塊或從後援協議屬性。 當接收端協議處理接收的訊息時，它根據訊息中的 ISA14 或 UNB9 值而產生技術通知。  
  
 如果協議中指定相關屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會預期 X12 或 EDIFACT 編碼的功能通知。 對於 X12，這個屬性是**預期 997**中**通知**頁面中，單向協議**協議屬性**對話方塊或從後援協議屬性。 對於 EDIFACT，這個屬性是**通知 (CONTRL) 必須是**屬性**通知**頁面中，單向協議**協議屬性**對話方塊中或從後援協議屬性。 當接收端協議處理接收的訊息時，它根據訊息中的 ISA14 或 UNB9 值而產生技術通知。  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收到 EDI 訊息的通知時，它會使用通知控制結構描述來驗證該通知。 這些結構描述包括 x12_<\<版本號碼\>_997.xsd 或 X12\_\<版本號碼\>對於 X12，EFACT _TA1.xsd\_\<版本號碼\>number>_contrl.xsd若為 EDIFACT，以及 HIPAA 5010 的 X12_00501_997.xsd。  
  
 當接收管線處理內送通知時，它會使該通知與已傳送的 EDI 交換相互關聯。 此管線會接著將該通知放入 MessageBox。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會處理進一步的通知。 除非您有針對它設定處理機制，否則該通知會進入擱置狀態。 若要處理該通知，您可以設定訂閱該通知的傳送埠，然後將該通知放入可定期刪除通知的資料夾。  
  
## <a name="see-also"></a>請參閱  
 [EDI 通知結構](../core/edi-acknowledgment-structure.md)   
 [傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md)