---
title: "設定簽章憑證 (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8539e210-1656-4fff-b026-36b81689061f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32a52962976c2db62de902906f53f5c270e2c7c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-signature-certificates-as2"></a>設定簽章憑證 (AS2)
在此頁面的設定中，您可以指定當外送訊息和 MDN 解析為此協議時，要用於簽署這些外送訊息和 MDN 的憑證。 此頁面上的設定會覆寫 BizTalk 群組屬性中提供的憑證設定。 如需有關如何使用憑證的詳細資訊，請參閱[Configuring certificates for AS2 憑證](../core/configuring-certificates-for-as2.md)。  
  
> [!IMPORTANT]
>  任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-agreement-level-signature-certificate"></a>若要設定協議層級的簽章憑證  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤上，按一下 **簽章憑證**。  
  
3.  選取**覆寫群組簽章憑證**使用此頁面中的憑證簽署外寄 AS2 訊息和 MDN 核取方塊。  
  
4.  按一下**瀏覽**顯示**選取憑證**對話方塊中，選取要套用此合作對象所傳輸訊息的簽章憑證的位置。  
  
5.  **一般名稱**文字方塊會顯示所選憑證的描述。  
  
6.  **指紋**文字方塊會顯示憑證的指紋。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。  
  
7.  按一下**移除憑證**若要移除選取的憑證。  
  
8.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)