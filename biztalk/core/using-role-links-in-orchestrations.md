---
title: "協調流程中使用角色連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role links
- roles, links
- roles
- roles, about roles
- role links, about role links
- role links, properties
- role links, initializing
ms.assetid: 0cf85544-12c9-4541-8925-61a6e946cce0
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e3c4e4a4c3a99fb6e1962299d440717eaa8d51b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-role-links-in-orchestrations"></a>在協調流程中使用角色連結
角色連結是協調流程與交易夥伴之間互動的抽象形式。 角色連結可讓您根據交易夥伴解析、訊息內容或資料庫尋查結果，動態選擇要與之互動的交易夥伴，而您的整體商務程序仍然能保持完整。  
  
 例如，在 B2B 實例中，有多個買方、一個供應商以及供應商的多個託運商。 當買方傳送訂單給供應商時，供應商透過合作對象解析知道是哪個買方傳送了這份訂單，並且可以套用適當的折扣。 此外，根據訂購的貨物，供應商還可以在執行階段決定將由哪個託運商負責運送。 雖然每個託運商各有自己的傳輸通訊協定，但供應商仍然可在執行階段使用相同的商務程序來處理所有託運商，並決定與哪個代理商進行互動。 在後續階段中，如果託運商更新其傳輸通訊協定 — 例如，從 FTP 變更為 HTTP — 供應商只需要使用 BizTalk 總管或 BizTalk Server 管理主控台來更新該特定託運商相關聯的傳送埠。 供應商則不需要變更其位於協調流程中的商務程序。  
  
## <a name="roles"></a>角色  
 在協調流程中有兩個角色：  
  
-   接收和處理訊息的「實作」角色。 這個角色也稱為提供者。  
  
-   傳送訊息的「使用」角色。 這個角色也稱為取用者。  
  
## <a name="role-links"></a>角色連結  
 角色連結可以包含取用者或提供者角色，或各有其一。 取用者角色會取用提供者角色提供的服務。 當您使用這兩個角色其中一個或兩者來定義角色連結時，它會假定互補角色是由您正在連結的夥伴擔任。  
  
 角色連結具有**SourceParty**屬性， **DestinationParty**屬性，以及初始角色。 初始角色是先進行通訊，以及因此啟始角色連結的值設定角色**DestinationParty**屬性。  
  
 如果初始角色是傳送訊息的取用者，則明確設定**DestinationParty**協調流程中的屬性 （一次，一次）。 若要這樣做，您可以設定的值**DestinationParty**中**運算式**圖形，如下列範例，其中 ConfirmOrder 是角色連結名稱，而 PartnerName 和 organizationname 則是合作對象的參數：  
  
```  
ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");  
```  
  
 如果初始角色是提供者接收訊息， **DestinationParty**屬性會自動初始化收件者。 **DestinationParty**設為提供者本身。 **SourceParty**屬性是唯讀的而且提供透過受信任的管線元件來解析合作對象名稱為基礎的安全性識別碼 (SID) 寄件者或合作對象相關聯的憑證。 執行管線元件的主控件必須標示為**信任的驗證**。 您可以取得的值**SourceParty**中**運算式**圖形，方法是使用下列範例程式碼：  
  
 `PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);`  
  
## <a name="role-link-types"></a>角色連結類型  
 角色連結是角色連結類型的執行個體，它是由一或兩個角色所組成。 使用角色連結類型時，請考量下列事項：  
  
-   您只能在單一角色連結類型中，參考任何指定的連接埠類型一次。  
  
-   因為角色連結類型定義包含連接埠類型，所以連接埠類型的範圍必須包含會使用它的任何角色連結類型的範圍。  
  
-   使用「商務活動服務」(BAS) 時，必須在與相關角色連結類型相同的 BizTalk 組件中定義結構化參數結構描述。 因為與結構描述有關聯的是角色連結類型，而非構成該角色連結類型的個別角色，如果兩個扮演不同角色的合作對象共用包含角色連結類型的組件，則雙方都會看見相同的結構化參數結構描述。 如果兩個合作對象都使用相同的角色連結類型，但是必須有不同的參數結構描述，則應該為每個合作對象建立不同的組件。 在每個組件中，角色連結類型則必須重複。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何在協調流程中建立角色連結](../core/how-to-create-role-links-in-orchestrations.md)  
  
-   [如何使用角色連結圖形](../core/how-to-use-the-role-link-shape.md)  
  
-   [如何使用角色連結精靈](../core/how-to-use-the-role-link-wizard.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md)   
 [協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)