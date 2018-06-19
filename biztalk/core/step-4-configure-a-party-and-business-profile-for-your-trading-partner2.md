---
title: 步驟 4： 設定合作對象與商務設定檔為您的交易夥伴 2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce07a1a6-4d5d-44ea-b1cb-04d7ae85747f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f775a720c6dcc42a3edd22154843a4a9118cc90e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278118"
---
# <a name="step-4-configure-a-party-and-business-profile-for-your-trading-partner"></a>步驟 4： 為交易夥伴設定合作對象與商務設定檔
![步驟 11-4](../core/media/tut-step4-of-11.gif "Tut_Step4_of_11")  
  
 在此步驟中，您會設定合作對象與商務設定檔，以便讓交易夥伴 Fabrikam 傳送 864 訊息至您的組織，並收到傳回的 997 通知訊息與非同步 MDN。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-a-party-and-business-profile-for-your-trading-partner"></a>若要為交易夥伴設定合作對象與商務設定檔  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台按一下**啟動**、 指向**所有程式**、 指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**.  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。 以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。  
  
3.  在**合作對象屬性**對話方塊方塊中，輸入**Fabrikam**中**名稱**欄位。  
  
4.  清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊。 清除核取方塊，即可指定合作對象 (在此情況下， **Fabrikam**) 未裝載 BizTalk Server。  
  
5.  按一下 **[確定]**。  
  
6.  以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。  
  
7.  在**設定檔屬性**對話方塊**一般**頁面上，輸入`Fabrikam_Profile`中**名稱**文字方塊。  
  
    > [!NOTE]
    >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在**一般**頁面上，指定設定檔的名稱。  
  
8.  按一下 **[確定]**。  
  
## <a name="next-steps"></a>後續步驟  
 您設定 BTS ISAPI 篩選器和 Fabrikam 和 Contoso 網頁中[步驟 5： 設定交易夥伴網頁](../core/step-5-configure-the-trading-partner-web-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 屬性](../core/configuring-edi-properties.md)