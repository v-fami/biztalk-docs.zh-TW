---
title: 步驟 3： 設定合作對象與商務設定檔為您 Organization1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 849e5146-a82a-41f2-bb96-089841b2444d
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5427ca12ff031bb7fa045a78709f97fdbb49fdb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023476"
---
# <a name="step-3-configure-a-party-and-business-profile-for-your-organization"></a>步驟 3： 為您的組織設定合作對象與商務設定檔
![步驟 3 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")  
  
 在此步驟中，您要為組織設定合作對象與商務設定檔，以便接收來自交易夥伴的 850 訊息，並傳回 997 通知訊息。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-a-party-and-business-profile-for-your-organization"></a>若要設定組織的合作對象與商務設定檔  
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**開始**、 指向**所有程式**，指向**Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。 以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。  
  
3. 在 **合作對象屬性**對話方塊方塊中，輸入**OrderSystem**中**名稱**欄位。  
  
4. 選取 **本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**核取方塊。 選取核取方塊，即可指定合作對象 (在此情況下， **OrderSystem**) 也裝載 BizTalk Server。  
  
5. 按一下 [確定] 。  
  
6. 以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。  
  
7. 在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入`OrderSystem_Profile`中**名稱**文字方塊。  
  
   > [!NOTE]
   >  當您建立合作對象時，名為設定檔*PartyName*（_p） 會自動建立。 您可以使用此設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在 **一般**頁面上，指定設定檔的名稱。  
  
8. 按一下 [確定] 。  
  
## <a name="next-steps"></a>後續步驟  
 您的夥伴組織設定合作對象與商務設定檔 (**Fabrikam**) 中所述[步驟 4： 為您的交易夥伴設定合作對象和商務設定檔](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 屬性](../core/configuring-edi-properties.md)