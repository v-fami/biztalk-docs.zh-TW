---
title: "如何復原 BizTalk Server 組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d39e50-4296-49c7-bd1e-63b1325af168
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9935c2c565d78d0bc102d4aef86959c2a9066e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-the-biztalk-server-configuration"></a>如何復原 BizTalk Server 組態
在復原 BizTalk Server 的過程中，您還必須匯入當初安裝 BizTalk Server 時所建立的組態檔。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
### <a name="to-recover-the-biztalk-server-configuration"></a>復原 BizTalk Server 組態  
  
1.  使用「記事本」編輯先前備份的 BizTalk Server 組態檔，然後輸入所有 BizTalk Server 服務的使用者帳戶密碼。  
  
2.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**。  
  
3.  在**Microsoft BizTalk Server 組態**，按一下 **匯入組態**。  
  
     確認所有功能的前面都沒有顯示無效圖示。 如果有任何功能發生組態錯誤，請立即修正錯誤。  
  
4.  按一下 [套用組態]。  
  
     設定完成所有 BizTalk Server 功能之後，請關閉組態視窗。  
  
## <a name="see-also"></a>另請參閱  
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)   
 [如何備份 BizTalk Server 組態](../core/how-to-back-up-the-biztalk-server-configuration.md)