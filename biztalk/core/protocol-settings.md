---
title: "通訊協定設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 224a9837-5c85-4511-b6d9-c8fda63a27d1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a8fe9e7024bfe3a9d5f1d5d7727a2115bcd31a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# 通訊協定設定
## 概觀
建立商務設定檔反映組織內的公司部門之後，企業需要宣告參數，定義商務設定檔之間如何進行通訊。 這些通訊參數均定義為通訊協定設定。 通訊協定設定可定義特定 B2B 通訊協定要如何支援商務交易。 每個商務設定檔定義每種 B2B 通訊協定處理訊息 (編碼) 或傳輸訊息 (傳輸) 的各種設定，讓夥伴能藉以通訊。 商務設定檔的通訊參數是依照下列兩種類別定義：  
  
-   **編碼通訊協定設定**: 編碼的通訊協定可掌控 B2B 訊息的內容與結構。 商務設定檔的編碼通訊協定設定可定義公司部門用來傳送和接收 B2B 訊息的編碼通訊協定。 編碼通訊協定的一些範例包括 X12、 EDIFACT、 HL7 等等。詳細的討論大約支援的編碼通訊協定所需的[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，請參閱[EDI 標準支援](../core/edi-standards-support.md)。 編碼通訊協定的一部分，您可以提供各種設定，例如是否傳送合作對象預期收到通知，訊息以批次還是個別傳送等等。您一律可以做為交易夥伴協議的一部分覆寫這些設定。 請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。  
  
-   **傳輸通訊協定設定**: 傳輸通訊協定可掌控用來傳送兩個夥伴之間往返的訊息的傳輸通道。 由於傳輸基本上是在兩個傳輸端點之間進行，所以每個商務設定檔都會定義自己的「傳輸端點」組態，然後與其交易夥伴之商務設定檔的單一「傳輸端點」通訊。 支援的傳輸通訊協定的相關資訊，請參閱[BizTalk Server 中的 AS2 支援](../core/as2-support-in-biztalk-server.md)。 傳輸通訊協定的一部分，您可以提供各種設定，例如是否訊息應該簽署，是否應該加密訊息等等。您一律可以做為交易夥伴協議的一部分覆寫這些設定。 如需協議的詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。  
  
 商務設定檔可透過定義通訊協定設定，宣告用來在交易夥伴之間傳送 B2B 訊息的訊息格式與傳輸通訊協定。  
  
> [!NOTE]
>  您可以選擇性在商務設定檔中定義通訊協定設定。 如果您未在商務設定檔中指定通訊協定，您永遠可以在協議中指定那些設定。  
  
 下圖示範交易夥伴、商務設定檔以及通訊協定設定在 TPM 解決方案中如何共同作用：  
  
 ![交易夥伴設定檔和通訊協定設定](../core/media/protocolsettings.gif "ProtocolSettings")  
  
 在上圖中，「出貨」商務設定檔可透過 AS2 傳輸通訊協定傳送和接收 X12 編碼格式的訊息。 同樣地，「發票」出貨設定檔可透過 AS2 傳輸通訊協定傳送和接收 X12 與 EDIFACT 編碼格式的訊息。  
  
 現在可明顯看出定義商務設定檔對於在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中建立 TPM 解決方案多有幫助。 目前如圖所示，「出貨」商務設定檔只能傳送和接收 X12 訊息。 因此，與「出貨」商務設定檔通訊的任何商務設定檔將必須符合「出貨」商務設定檔的屬性設定。 不過，在未來，如果 「 出貨 」 商務設定檔開始接受與 EDIFACT 編碼訊息時，它只需要設定相關的屬性，以包含 EDIFACT 支援。 夥伴組織不需要為相同的出貨部門建立新的商務設定檔。  
  
## 我是否一定需要建立商務設定檔時指定的通訊協定設定？  
 理論上是的，商務設定檔必須包含通訊協定定義。 不過，這不表示您在以 TPM 使用者介面建立商務設定檔時必須定義通訊協定設定。 TPM 可讓您彈性地在建立商務設定檔或建立交易夥伴協議時，指定通訊協定設定。 如果您在商務設定檔中定義通訊協定設定，當您在為該設定檔建立交易夥伴協議時，就可以使用那些設定。 不過，如果您在協議中訂通訊協定設定，則必須在協議中提供所有的值。  
  
> [!IMPORTANT]
>  如果您未在商務設定檔中定義通訊協定設定，則您將需要為該商務設定檔在每個協議中輸入值，藉以定義新 TPM 解決方案的延展性模型。 因此，Microsoft 建議您為每個商務設定檔定義通訊協定設定。 您永遠可以視需要在建立交易夥伴協議時，覆寫那些設定。  

## 了解接下來
[交易夥伴協議](../core/trading-partner-agreement.md)  
[整合在一起： 定義交易夥伴管理解決方案](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)  
  
## 另請參閱  
 [交易夥伴管理方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)