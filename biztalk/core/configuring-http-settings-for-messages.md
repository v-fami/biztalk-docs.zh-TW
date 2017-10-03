---
title: "設定訊息的 HTTP 設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ed400f1-561d-4812-adf1-20e4300fd048
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d15ebb5ff5be6678c4dc2aee3f9333f36c75c89f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-http-settings-for-messages"></a>設定訊息的 HTTP 設定
在訊息相關的 HTTP 設定中，您可以指定接收 AS2 訊息之 Web 伺服器預期的屬性。  
  
> [!IMPORTANT]
>  任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-message-related-http-settings"></a>設定訊息相關的 HTTP 設定  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**本機主機設定**區段中，按一下**訊息的 HTTP 設定**。  
  
3.  選取**忽略 SSL 憑證名稱不符**核取方塊，以確保如果伺服器名稱不符合為其產生 SSL 憑證的伺服器名稱，SSL 連接會仍會接受。  
  
4.  按一下**HTTP 需要 100 繼續**HTTP Expect 標頭設定為 100-繼續進行，以指定在初始 HTTP 要求中，而會等待伺服器要求內容不包含張貼的資料。  
  
5.  按一下**保持 HTTP 連線運作**要求 HTTP 連線在要求和回應循環完成之後會保持運作。  
  
6.  按一下**展開 HTTP 標頭**到 HTTP content-type 標頭展開至單一行。  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定本機主機設定 (AS2)](../core/configuring-local-host-settings-as2.md)