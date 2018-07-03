---
title: 使用失敗訊息的訂用帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- failed messages, subscriptions
- failed messages, developing
- developing, failed message subscriptions
ms.assetid: 8dee0aa8-53bf-40be-866b-f1b83960dc99
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e4cedf2d47c0bbe8e812795ad428a987d4c2014
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014215"
---
# <a name="working-with-failed-message-subscriptions"></a>使用失敗的訊息的訂用帳戶
當 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]解譯器處理序 （剖析和驗證） 訊息時，它會升級該訊息的屬性。 如果 A4SWIFT 接收訊息的輸入批次的一部分，這些升級的屬性會提供資訊的正確性與訊息的有效性，以及批次的相關資訊。 如需這些屬性的完整清單，請參閱 < [A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
 不同於原生 BizTalk 解譯器，A4SWIFT 解譯器不會暫停處理會產生錯誤或失敗時訊息。 相反地，它會發佈失敗的訊息至 MessageBox 資料庫就像一樣是有效的訊息。 如此一來，失敗的訊息可以包含到 MessageBox 資料庫的錯誤詳細資料。 您可以從 MessageBox 資料庫擷取訊息、 處理和修復的訊息和回 MessageBox 資料庫，甚至重新提交訊息。 您會無法執行大部分的這些工作，如果訊息是實際上*暫止*。  
  
 您可以識別 A4SWIFT 已由其升級屬性發佈到 MessageBox 資料庫為失敗或發生錯誤的訊息。 在處理失敗的訊息時，SWIFT 解譯器會填入，並將升級**A4SWIFT_Failed**屬性，以及其中一個或多個其他下列屬性，再將訊息發佈至 MessageBox 資料庫：  
  
- **A4SWIFT_ParseErrors**指出剖析錯誤 （例如格式不正確的資料），在處理期間發現的數字。  
  
- **A4SWIFT_XmlValidationErrors**指出 XML 驗證錯誤 （例如無效的資料或不正確的類型，相對於結構描述） 在處理期間發生的數目。  
  
- **A4SWIFT_BreValidationErrors**指出在處理期間發生的商務規則引擎 (BRE) （例如中斷的 SWIFT 網路規則的資料） 的驗證錯誤的數目。  
  
- **A4SWIFT_Failed**已 **，則為 true**計數時的任何上述屬性小於或等於零，或**false**當計數等於零。  
  
  這些屬性是 Microsoft 的所有組件。Solutions.A4SWIFT.Property 命名空間。 如需有關這些和其他升級的屬性的詳細資訊，請參閱 < [A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
  若要攔截或擷取失敗的訊息，您要建立篩選條件運算式 （訂閱） 傳送埠或協調流程接收圖形，包括一些上面所列的屬性為**AND**子句的運算式。  
  
  例如，若要訂閱的所有失敗訊息，您要加入下列子句 (作為**AND**子句如果沒有其他子句):  
  
  Microsoft。Solutions.A4SWIFT.Property.A4SWIFT_Failed = = **，則為 true**  
  
  若要訂閱只能剖析失敗的訊息，您加入下列子句執行下列在一起：  
  
  **和**Microsoft。Solutions.A4SWIFT.Property.A4SWIFT_Failed = =**真**，**AND**Microsoft。Solutions.A4SWIFT.Property.A4SWIFT_XmlValidationErrors = = 0，**AND**Microsoft。Solutions.A4SWIFT.Property.A4SWIFT_BreValidationErrors = = 0;  
  
  相反地，針對傳送埠或協調流程設計用來處理有效的訊息，包括 「**AND**Microsoft。Solutions.A4SWIFT.Property.A4SWIFT_Failed = = **false**"做為其篩選條件運算式中的子句。  
  
> [!NOTE]
>  如果訂用帳戶重疊，A4SWIFT 會滿足所有訂用帳戶。 也就是說，如果 （傳送埠或協調流程） 的多個服務有滿足特定訊息的篩選條件運算式，所有這類服務會收到相同的訊息。 比方說，如果傳送埠訂閱所有失敗的訊息，以及協調流程會訂閱具有剖析失敗的唯一訊息，這兩個訂用帳戶會滿足 A4SWIFT 處理訊息時，發生剖析錯誤時。 請務必在服務間消除不必要的重疊，訂用帳戶中。  
> 
> [!NOTE]
>  A4SWIFT 如果 A4SWIFT 接收和處理訊息，並將該訊息發佈到 MessageBox 資料庫，但訊息不符合任何訂用帳戶，將會擱置訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]錯誤，指出缺少的 「 訂閱者 」。 比方說，如果您有訂閱的所有訊息的服務 」 A4SWIFT_Failed = = false"，但沒有服務訂閱訊息，"A4SWIFT_Failed = = true"，則無法剖析的訊息或驗證即確實會暫止的訂閱者的不足。 這種情況下實際上可讓您模擬傳統擱置失敗的訊息。 請務必訂閱所有您不希望有擱置的訊息。 如需 MessageBox 資料庫的訂用帳戶的其他詳細資料請參閱 BizTalk Server 說明、 傳送埠、 協調流程，和篩選條件運算式。  
  
 此部分包含：  
  
-   [失敗的訊息和 ErrorCollection 物件](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)