---
title: 交易夥伴和商務設定檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cbeac421-c319-4a60-a188-28f7268888fc
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fff632199d3acd8be4ade7724eaa49748dab5db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279534"
---
# <a name="trading-partners-and-business-profiles"></a>交易夥伴與商務設定檔

## <a name="overview"></a>概觀
商務關係中的每個參與組織都是交易夥伴。 交易夥伴也稱為「交易合作對象」或「合作對象」，在交易夥伴方案中位於根層級，並且是交易夥伴方案的基礎。 交易夥伴是指在一段由兩個以上參與者組成的進行中商務關係的其中一個參與者。 交易夥伴是指任何可與其他合作夥伴往返傳送訊息的單一商務實體。  
  
 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，TPM 方案可以用來模型化及儲存任何交易夥伴的資訊，例如傳送埠關聯和憑證用來驗證合作對象的識別。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用此資訊來處理收到的訊息和傳送訊息。 每個組織參與商務關係，包括主要組織 (執行本機主機組織[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機)，表示為交易夥伴。
  
 ![交易合作對象](../core/media/tradingparties.gif "TradingParties")  
  
 例如，請考慮兩個組織： Fabrikam 和 Contoso。 使用 Fabrikam [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 若要使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來管理所有與 Contoso 進行的商務資料交換，Fabrikam 必須建立兩個交易夥伴：一個代表自己，一個代表 Contoso。 在建立合作對象時，您會提供特定詳細資料，例如夥伴名稱，以及等等。  
 
## <a name="business-profiles"></a>商務設定檔

交易夥伴的商務設定檔 (亦稱為商務設定檔)，是組織的商務面孔。 組織內每個與其他組織內的其他業務部門往來交易的業務部門，都會以 TPM 方案中的某個商務設定檔表示。 商務部門、商務單位或商務系統所有專屬用來定義 B2B 傳訊參數的屬性，都會放在其商務設定檔中。 例如，假設 Fabrikam 有兩個商務部門: 「 出納 」 和 「 出貨 」。 Contoso 有一個商務部門"Invoices"。 假設 Fabrikam 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，就必須建立：  
  
-   兩個商務設定檔，每個各自代表交易夥伴 Fabrikam 下的 Payment 和 Shipping 部門。  
  
-   一個商務設定檔，代表交易夥伴 Contoso 下的 Invoice 部門。  
  
 下圖說明如何在 TPM 方案中管理夥伴與商務設定檔：  
  
 ![交易夥伴的商務設定檔](../core/media/businessprofile.gif "BusinessProfile")  
  
 定義商務設定檔之後，商務部門就可以定義其在傳送或接收 B2B 訊息時，必須使用的訊息編碼格式和傳輸方式。 中會討論這些商務設定檔之間的通訊模式[通訊協定設定](../core/protocol-settings.md)。  
  
### <a name="why-do-i-need-business-profiles"></a>為什麼需要商務設定檔？  
 商務設定檔可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用者在 TPM 解決方案中更完整地呈現它們的商務模型。 擁有多個商務部門的企業在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中可以有獨立的表示方式。 更重要的是，此模型可讓使用者針對每個商務設定檔設定屬性，以定義該商務設定檔如何與其他設定檔交易。 例如，假設企業在美國和歐洲各有一個部門。 在美國的部門預期 EDI 訊息只會以 X12 標準，而在歐洲的部門預期 EDI 訊息只會以 EDIFACT 標準。 藉由建立合作對象，企業可以設定的正確的傳訊屬性層級設定檔，並同時使用已設定夥伴層級的屬性。 沒有商務設定檔，企業就必須建立所有的商務部門的交易夥伴，然後複製一堆屬性到這些交易夥伴。  
  
 您也可以將商務識別與商務設定檔產生關聯，以產生唯一的識別碼。 這些商務實體可以由標準機關提供，也可以由商務識別手動同意。  
  
> [!IMPORTANT]
>  如果同一組織內的兩個商務部門需要彼此交易，必須為他們各建立一個交易夥伴。 同一夥伴下的兩個設定檔不能彼此交易，因為交易夥伴關係只能在不同的夥伴之間存在。  
  
## <a name="learn-next"></a>了解接下來

[通訊協定設定](../core/protocol-settings.md)  
[交易夥伴協議](../core/trading-partner-agreement.md)  
[整合在一起： 定義交易夥伴管理解決方案](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)
 
## <a name="see-also"></a>另請參閱  
 [交易夥伴管理方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)