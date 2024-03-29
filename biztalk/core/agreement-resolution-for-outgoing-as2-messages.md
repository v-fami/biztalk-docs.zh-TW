---
title: 外寄 AS2 訊息的協議解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 578d7565-534c-4c13-b473-975f347f3a9b
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce8329b2b80ca3b9bfd6b34379d936d6be1df3ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975855"
---
# <a name="agreement-resolution-for-outgoing-as2-messages"></a>外寄 AS2 訊息的協議解析
當 AS2 傳送管線處理透過 HTTP/HTTPS 傳輸的外寄 EDIINT/AS2 編碼訊息時，它會判斷該訊息將解析的協議。 它接著會使用這些協議屬性來處理外寄訊息。 傳送管線會使用下列準則來判斷協議 (依優先順序)：  
  
1. 傳送管線會嘗試將 AS2From 和 AS2To 的內容屬性與指定為協議屬性一部分之 AS2From 和 AS2To 的值進行比對。  
  
2. 如果上一個步驟失敗，傳送管線會嘗試比對輸出訊息的 AS2To 內容屬性，與 AS2To 屬性，做為其他的協議解析程式中設定的值**識別碼**協議索引標籤屬性。  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不會將 AS2To 屬性寫入內容。 如果您想對 AS2To 內容屬性執行協議解析，必須併入自訂協調流程或自訂管線元件才行。 如需詳細資訊，請參閱 <<c0> [ 撰寫 AS2 內容屬性，以執行輸出合作對象解析](../core/writing-as2-context-properties-for-outbound-party-resolution.md)。  
   > 
   > [!NOTE]
   >  當您使用動態傳送埠時，必須將 AS2To 屬性寫入至內容才能進行協議解析。  
  
3. 如果上述步驟失敗，傳送管線會嘗試比對與協議關聯的傳送埠以及訂閱訊息的傳送埠。 傳送埠是中的協議相關聯**傳送埠**頁面的單向 AS2 協議**協議屬性** 對話方塊。  
  
   > [!NOTE]
   >  與 EDI 處理不同的是，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議時，沒有可用的後援 AS2 屬性。 不過，有預設的協議可用來傳送 MDN。 此外，也不會使用傳送埠或 Http.UserHttpHeaders 內容屬性來解析 MDN 的協議。 如需詳細資訊，請參閱的 「 協議解析 MDN > 一節[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。  
   > 
   > [!NOTE]
   >  如果 AS2-To 協議屬性中**識別碼**頁面的單向 AS2 協議**協議屬性**預設為英文的合作對象名稱，而 AS2 中的值設定對話方塊-To 標頭AS2 訊息設定為非英文名稱，則會找不到相符項目。  
  
> [!NOTE]
>  透過 AS2 傳送 EDI 時，您必須針對 EDI 和 AS2 使用不同的協議。  
  
 如需傳送程序的詳細資訊，請參閱 <<c0> [ 產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何傳送 AS2 訊息](../core/how-biztalk-server-sends-as2-messages.md)