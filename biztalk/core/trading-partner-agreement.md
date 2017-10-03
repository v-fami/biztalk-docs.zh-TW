---
title: "交易夥伴協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e40a3847-ee36-4a75-ab50-def9b0caf07e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a62ada3317bc347a6d39af9fb2f983e02647e5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="trading-partner-agreement"></a>交易夥伴協議
## <a name="overview"></a>概觀
交易夥伴協議 (TPA) 的定義是，兩個交易夥伴之間透過特定 B2B 通訊協定交易訊息時所採用的決定性與繫結性協議。 協議會將在雙方合作對象所屬商務設定檔中共同的雙向訊息處理屬性收集在一起。 這完整收集了兩個交易夥伴之間進行商務交易時受制於的所有層面。 TPA 通常是透過設定每個合作夥伴的設定檔而產生，並可讓人自訂和覆寫必要設定。  
  
 簡單地說，TPA 指的是當兩個商務設定檔互相交換 B2B 訊息時，對於使用特定訊息編碼通訊協定或特定傳輸通訊協定的一種共識。  
  
 ![夥伴設定檔與協議](../core/media/tradingpartneragreement.gif "TradingPartnerAgreement")  
  
 在上圖中，沒有之間的"Shipping"和"Invoice"設定檔的 Fabrikam 和 Contoso 的協議，分別為使用 X12 編碼的商務訊息 (**編碼協議**) 和 AS2 傳輸交換訊息 (**傳輸協議**)。 許多商務設定檔之間都可能會有這類協議。 例如，“Payments” 和 “Invoice” 設定檔之間可能會有一個使用 EDIFACT 訊息編碼標準的協議。 所有這類協議的所有設定檔的兩個交易夥伴構成**合作關係**兩個交易夥伴。  
  
## <a name="bi-directional-agreements"></a>雙向協議  
 兩個商務設定檔之間的每個協議都是雙向協議。 例如，“Shipping” 和 “Invoice” 商務設定檔之間的協議將會包含屬性來處理下列訊息：  
  
-   “ Shipping” 設定檔從 “ Invoice” 設定檔那邊收到的訊息，以及  
  
-   “ Shipping” 設定檔 傳送給 “ Invoice” 設定檔的訊息  
  
 簡單地說，雙向協議就是兩個單向協議的集合。 其中一個單向協議可以想成一組屬性，這些屬性定義了合作對象 A 到合作對象 B 的訊息交易方式。而另一個單向協議則可以想成另一組屬性，這些屬性定義了合作對象 B 到合作對象 A 的訊息交易方式。  
  
## <a name="considerations-when-defining-an-agreement"></a>定義協議時的考量  
 在建立交易夥伴協議時，您必須考慮下列各點：  
  
-   對於兩個彼此交換 B2B 訊息的商務設定檔，必須定義一個訊息編碼協議。 合作單位可以僅在需要使用 AS2 通訊協定來彼此傳輸訊息時，才選擇擁有 AS2 協議。 例如，如果商業單位之間選擇透過電子郵件來傳輸訊息，就不需要有 AS2 協議。  
  
-   如果有兩個商務設定檔都支援 X12 和 EDIFACT 編碼，而且這兩個商務設定檔都同意使用這兩個編碼通訊協定來交換訊息，則每個通訊協定應該要有各自的協議。 X12 通訊協定應該要有一個協議，而 EDIFACT 通訊協定應該要有另一個協議。 兩個通訊協定不能共用一個協議。  
  
-   X12 與 EDIFACT 訊息的編碼協議不能和 AS2 的傳輸協議屬於同一個協議。 您必須為兩者建立個別的協議。  
  
## <a name="global-or-fallback-agreement"></a>全域或後援協議  
 某些商業組織可能選擇只擁有一套 B2B 處理機制，而不管參與特定 B2B 訊息傳遞的夥伴是誰。 實際上，這類商業組織只會有一個與其他所有交易夥伴分享的通用 B2B 通訊協定設定。 此外，因為這類組織不需要針對特定夥伴有特定的設定，所以 B2B 通訊協定設定是針對交易夥伴進行定義，而不是針對交易商務設定檔。 在[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，這類商業組織會反映為**全域交易夥伴**。 其他企業在需要交易時，表示為全域交易夥伴的商務使用稱為 「 全域交易夥伴協議**全域交易夥伴協議**。 這些協議符合針對全域交易夥伴定義的訊息編碼和通訊協定設定。  
  
 當兩個交易夥伴之間在設定檔層級建立的通訊協定設定彼此配合不上，而無法形成交易夥伴協議時，這些在全域層級定義的設定也很有用。 在這種情況下，裝載 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 的組織可以根據針對合作夥伴定義的通訊協定設定，使用另一個交易商務設定檔來形成協議。 在使用交易夥伴就稱為所定義的全域通訊協定設定，在這種情況下，達成的協議**後援交易夥伴協議**。  

## <a name="learn-next"></a>了解接下來

[融會貫通： 定義交易夥伴管理解決方案](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)
  
## <a name="see-also"></a>另請參閱  
 [交易夥伴管理方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)