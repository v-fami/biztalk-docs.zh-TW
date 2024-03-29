---
title: 步驟 4： 設定交易的 partner1 的合作對象與商務設定檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db50d0f6-e838-4e92-8548-a63a2c445d55
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa53034af1a07ca55574e2e37eecb7c0875f8a2e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989679"
---
# <a name="step-4-configure-a-party-and-business-profile-for-your-trading-partner"></a>步驟 4： 為交易夥伴設定合作對象與商務設定檔
![步驟 4 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")  
  
 在此步驟中，您要設定合作對象與商務設定檔，以便讓交易夥伴 Fabrikam 傳送 850 訊息至您的組織，並收到傳回的 997 通知訊息。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-a-party-and-business-profile-for-your-trading-partner"></a>若要為交易夥伴設定合作對象與商務設定檔  
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**開始**、 指向**所有程式**，指向**Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。 以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。  
  
3. 在 **合作對象屬性**對話方塊方塊中，輸入**Fabrikam**中**名稱**欄位。  
  
4. 清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**核取方塊。 清除核取方塊，即可指定合作對象 (在此情況下， **Fabrikam**) 未裝載 BizTalk Server。  
  
5. 按一下 [確定] 。  
  
6. 以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。  
  
7. 在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入`Fabrikam_Profile`中**名稱**文字方塊。  
  
   > [!NOTE]
   >  當您建立合作對象時，名為設定檔*PartyName*（_p） 會自動建立。 您可以使用此設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在 **一般**頁面上，指定設定檔的名稱。  
  
8. 按一下 [確定] 。  
  
## <a name="next-steps"></a>後續步驟  
 您設定接收位置 (**fromTHEM_4010_850**) 中所述，從 Fabrikam 接收 850 訊息[步驟 5： 設定接收埠和接收位置](../core/step-5-configure-a-receive-port-and-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 屬性](../core/configuring-edi-properties.md)