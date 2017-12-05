---
title: "使用失敗訊息的訂用帳戶 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed messages, subscriptions
- failed messages, developing
- developing, failed message subscriptions
ms.assetid: 8dee0aa8-53bf-40be-866b-f1b83960dc99
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6540259fd6983fd418e57ff700de3f1b550016ec
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="working-with-failed-message-subscriptions"></a>使用失敗的訊息的訂閱
當[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]解譯器處理序 （剖析及驗證） 訊息時，它會升級屬性，該訊息。 如果 A4SWIFT 收到訊息做為輸入的批次的一部分，這些升級的屬性會提供資訊的正確性與有效的訊息，以及批次相關資訊。 如需這些屬性的完整清單，請參閱[A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
 不像原生 BizTalk 解譯 A4SWIFT 解譯器不會暫停訊息處理，便會產生錯誤或失敗時。 相反地，它失敗將訊息發佈到 MessageBox 資料庫就像是有效的訊息。 如此一來，失敗的訊息可包含至 MessageBox 資料庫的錯誤詳細資料。 您可以從 MessageBox 資料庫擷取訊息、 處理和修復訊息，且即使重新提交訊息到 MessageBox 資料庫。 您不能執行大部分的這些工作，如果訊息是實際*暫停*。  
  
 您可以識別 A4SWIFT 具有其升級屬性發佈至 MessageBox 資料庫為失敗或錯誤訊息。 SWIFT 解譯器在處理失敗的訊息時，會填入，並且將升級**A4SWIFT_Failed**屬性，以及一或多個其他下列屬性，然後再將訊息發佈至 MessageBox 資料庫：  
  
-   **A4SWIFT_ParseErrors**指出的剖析錯誤 （例如格式不正確的資料），在處理期間發生數目。  
  
-   **A4SWIFT_XmlValidationErrors**指出 XML 驗證錯誤 （例如無效的資料或不正確的類型，相對於結構描述） 在處理期間發生的數目。  
  
-   **A4SWIFT_BreValidationErrors**指出在處理期間發現的商務規則引擎 (BRE) （例如中斷 SWIFT 網路規則的資料） 的驗證錯誤數目。  
  
-   **A4SWIFT_Failed**是**true**計數時的任何上述屬性小於或等於零，或**false**當計數等於零。  
  
 這些屬性都是屬於[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.A4SWIFT.Property 命名空間。 如需有關這些和其他升級的屬性的詳細資訊，請參閱[A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
 若要攔截或擷取失敗的訊息，您需要建立篩選條件運算式 （訂閱） 傳送埠或協調流程接收圖形包含某些上面所列的屬性做為**AND**子句的運算式。  
  
 例如，若要訂閱所有失敗的訊息，您加入下列子句 (做為**AND**子句如果沒有其他子句):  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.A4SWIFT.Property.A4SWIFT_Failed = = **，則為 true**  
  
 若要訂閱只剖析失敗的訊息，將下列子句一起：  
  
 **和** [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.A4SWIFT.Property.A4SWIFT_Failed = = **true**，**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.A4SWIFT.Property.A4SWIFT_XmlValidationErrors = = 0，**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.A4SWIFT.Property.A4SWIFT_BreValidationErrors = = 0;  
  
 相反地，針對傳送埠或協調流程設計用來處理有效的訊息，包括 「**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.A4SWIFT.Property.A4SWIFT_Failed = = **false**"做為其篩選條件運算式中的子句。  
  
> [!NOTE]
>  如果訂閱重疊，A4SWIFT 都滿足所有訂用帳戶。 也就是說，如果 （傳送埠或協調流程） 的多個服務有特定的訊息可滿足篩選條件運算式，所有此類服務會收到相同的訊息。 比方說，如果所有失敗訊息的傳送埠訂閱協調流程會訂閱僅發生剖析錯誤的訊息，這兩種訂閱將滿足 A4SWIFT 處理訊息時，遇到剖析發生錯誤時。 請務必排除在服務間的訂用帳戶中的不想要的重疊。  
  
> [!NOTE]
>  A4SWIFT 如果 A4SWIFT 接收和處理訊息，並將該訊息發佈到 MessageBox 資料庫，但是訊息不符合任何訂用帳戶，將會擱置訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]指出缺乏 「 訂閱者 」 的錯誤。 比方說，如果您有訂閱的所有訊息的服務 」 A4SWIFT_Failed = = false"，但沒有任何服務訂閱訊息其中"A4SWIFT_Failed = = true"，則無法剖析的訊息或驗證會確實被暫止的 「 訂閱者 」 的不足。 這種情況下確實可讓您模擬傳統擱置失敗的訊息。 請務必訂閱所有您不希望有擱置的訊息。 如需 MessageBox 資料庫訂閱的其他詳細資料請參閱 BizTalk Server 說明、 傳送埠、 協調流程，和篩選條件運算式。  
  
 此部分包含：  
  
-   [失敗的訊息和 ErrorCollection 物件](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)