---
title: "如何在協調流程中建立角色連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc386ac2-a851-4342-9ceb-0b6faddf4ece
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e40a77392af9e97791cd9afbacc8f0b533f60288
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-role-links-in-orchestrations"></a>如何在協調流程中建立角色連結
以下是您要在協調流程中使用角色連結時所需完成的基本工作：  
  
-   建立合作對象與傳送埠，並將它們彼此關聯。  
  
-   請使用下列程序來建立角色連結類型及新增連接埠類型。  
  
    |建立角色連結類型|  
    |--------------------------------|  
    |1.在 協調流程檢視 視窗中，依序展開**類型**，以滑鼠右鍵按一下**角色連結類型**，然後按一下 **新角色連結類型**。<br />2.按一下您剛建立的角色連結類型。 在 [屬性] 視窗中**識別碼**欄位中，輸入`Provider_Consumer_RoleLinkType`。<br />3.展開**provider_consumer_rolelinktype**，然後按一下  **role_1**。 在 [屬性] 視窗中**識別碼**欄位中，輸入`ConsumerRole`。<br />4.以滑鼠右鍵按一下**ConsumerRole**，然後按一下 **新增連接埠類型**。 如此便可啟動「連接埠類型精靈」。<br />5.在**歡迎使用連接埠類型精靈**頁面上，按一下**下一步**。<br />6.在**選取連接埠類型或建立新的連接埠類型**頁面上，選取**建立新的連接埠類型**，然後**連接埠類型名稱**，型別`ConsumerPortType`。<br />7.如**通訊模式**，選取**單向**，以及**存取限制**，選取**公用-沒有限制**。 按一下 **[下一步]**。<br />8.在**完成連接埠精靈**頁面上，按一下**完成**。<br />9.以滑鼠右鍵按一下**provider_consumer_rolelinktype**，然後按一下 **新角色**。<br />10.按一下**[role_1]**，然後在 [屬性] 視窗中**識別碼**欄位中，輸入`ProviderRole`。<br />11.以滑鼠右鍵按一下**ProviderRole**，然後按一下 **新增連接埠類型**。 如此便可啟動「連接埠類型精靈」。<br />12.在**歡迎使用連接埠類型精靈**頁面上，按一下**下一步**。<br />13.在**選取連接埠類型或建立新的連接埠類型**頁面上，選取**建立新的連接埠類型**，然後**連接埠類型名稱**，型別`ProviderPortType`。<br />14.如**通訊模式**，選取**單向**，以及**存取限制**，選取**公用-沒有限制**。 按一下 **[下一步]**。<br />15.在**完成連接埠精靈**頁面上，按一下**完成**。 **注意：**放置在角色連結的已設定連接埠不會保留其相關聯的繫結資訊。|  
  
     在前面的程序中，您建立了包含兩個角色的角色連結類型，分別是會接收及處理取用者傳來之訊息的 ProviderRole，以及您的協調流程將使用隨角色提供之傳送埠來傳送訊息給取用者的 ConsumerRole。  
  
> [!NOTE]
>  角色連結類型可以包含提供者角色和取用者角色，而且可以包含任一個角色，或兩種角色各一個 (視您的商務程序需求而定)。  
  
-   使用下列程序，將角色連結新增至您的協調流程。  
  
    |若要使用角色連結精靈建立角色連結|  
    |---------------------------------------------------------|  
    |1.在協調流程 [工具箱] 中，拖曳**角色連結**圖形至設計介面。 如此便可啟動「角色連結精靈」。<br />2.在**歡迎使用角色連結精靈**頁面上，按一下**下一步**。<br />3.在**角色連結名稱**頁面上，於**名稱**欄位中，輸入`Provider_Consumer`。 按一下 **[下一步]**。<br />4.在**角色連結類型**頁面上，選取**使用現有的角色連結類型**。 在**角色連結類型名稱**下拉式清單中，選取**[provider_consumer_rolelinktype]**。 按一下 **[下一步]**。<br />5.在**角色識別**頁面上，選取**ProviderRole**從**此協調流程將實作哪一個角色來接收和處理來自夥伴的訊息？**下拉式清單。 精靈會自動選取**ConsumerRole**如**此協調流程會將訊息傳送至夥伴角色內的連接埠上使用下列角色**。 按一下 **[下一步]**。<br />6.在**角色連結使用方式**頁面上，選取**我將會傳送第一個訊息給我夥伴的角色**。 按一下 **[完成]**。|  
  
     在前面的程序中，您已進一步將 ConsumerRole 定義為初始角色。 . 這表示您的協調流程會透過 ConsumerRole 所提供的連接埠將第一個訊息傳送給取用者，然後 ProviderRole 會接收從取用者所傳回的訊息，以做進一步的處理。  
  
    > [!NOTE]
    >  如果角色連結類型中只有一個角色，您需要您的角色定義商務程序中，選取**提供者角色： 我將會接收第一個訊息**或**取用者角色： 我將會傳送第一個訊息**而不是執行步驟 5 中前述程序。  
  
-   設計您的商務程序。 您可以利用相互關聯集合來確保內送訊息與適當的協調流程執行個體是相符的。  
  
-   關聯連接埠與**傳送**和**接收**圖形。 此外，請執行下列動作：  
  
    -   如果初始角色是傳送訊息的取用者，明確地設定**DestinationParty**協調流程中的屬性 （一次，一次）。 若要這樣做，請將設定的值**DestinationParty**中**運算式**圖形，如下列範例，其中 ConfirmOrder 是角色連結名稱，而 PartnerName 和 organizationname 則是參數合作對象：  
  
        ```  
        ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");  
        ```  
  
    -   如果初始角色是提供者接收訊息， **DestinationParty**屬性會自動初始化收件者。 **DestinationParty**設為提供者本身。 **SourceParty**屬性是唯讀的而且提供透過受信任的管線元件來解析合作對象名稱為基礎的安全性識別碼 (SID) 寄件者或合作對象相關聯的憑證。 執行管線元件的主控件必須標示為**信任的驗證**。 您可以取得的值**SourceParty**中**運算式**圖形，方法是使用下列範例程式碼：  
  
        ```  
        PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);  
        ```  
  
## <a name="examples-of-using-role-links"></a>使用角色連結的範例  
  
-   [PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)  
  
-   從 BizTalk Server 程式碼範例，可從下載 SDK 範例 「 使用角色連結 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)   
 [如何使用角色連結圖形](../core/how-to-use-the-role-link-shape.md)   
 [如何使用角色連結精靈](../core/how-to-use-the-role-link-wizard.md)