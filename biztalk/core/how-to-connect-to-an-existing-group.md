---
title: 如何連接到現有的群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.connecttogroup
helpviewer_keywords:
- groups, existing
- groups, connecting
- managing [groups], connecting
ms.assetid: 1eedbcd5-f3f1-4da5-b91c-67377131f889
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e29b57f39ab1cb86e34a9e744063ff248d12ad1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994351"
---
# <a name="how-to-connect-to-an-existing-group"></a>如何連接至現有的群組
您可以使用企業中任何電腦上的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，從遠端管理企業內一或多個 BizTalk Server 群組，只要這些群組位於相同網域或信任網域中的電腦上。  
  
 在 BizTalk Server 管理主控台中的 [BizTalk Server 管理] 節點是所有的 BizTalk 群組的最高層級節點，將現有的 BizTalk Server 群組加入至 BizTalk Server 管理主控台時，您使用的層級。 在新增群組時，必須指定您要連接的現有伺服器與「BizTalk 管理」資料庫。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員登入，或以「BizTalk Server 系統管理員」群組的成員登入。  
  
### <a name="to-connect-to-an-existing-group"></a>連接至現有的群組  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，以滑鼠右鍵按一下**BizTalk Server 管理**，然後按一下**連接到現有的群組**。  
  
3. 在 **連接到現有的 BizTalk Server 組態資料庫**對話方塊的  **SQL Server 名稱**下拉式清單方塊中，選取裝載 BizTalk 的 Microsoft SQL Server 執行個體的名稱管理資料庫 （也稱為 「 組態 」 資料庫）。 當您選取 SQL Server 執行個體時，BizTalk Server 會自動嘗試偵測位於該電腦上的 BizTalk Server 資料庫。  
  
4. 在 **資料庫名稱**下拉式清單方塊中，選取 BizTalk Server 管理資料庫 (**BizTalkMgmtDb**) 至您要連接，，然後按一下**確定**。  
  
    BizTalk Server 管理主控台會將 BizTalk Server 群組加入主控台樹狀目錄中。  
  
   > [!NOTE]
   >  如果 BizTalk Server 管理資料庫位於 SQL Server 叢集上，而叢集正在進行容錯移轉，那麼當您嘗試連接管理資料庫時，就可能收到類似下列的錯誤：  
   >   
   >  無法載入群組 [\<servername\>:\<管理資料庫\>] 資料提供者。  
   >   
   >  And  
   >   
   >  其他資訊:  
   >   
   >  找不到 WMI 類別的執行個體。 (WinMgmt)  
   >   
   >  發生這個錯誤的原因，是因為在進行容錯移轉時，無法使用 BizTalk 資料庫。 若要解決這個問題，請等到 SQL Server 的叢集執行個體上線後，再嘗試使用 BizTalk Server 管理主控台連線到它。  
  
## <a name="see-also"></a>另請參閱  
 [管理群組](../core/managing-groups.md)   
 [BizTalk 群組](../core/biztalk-groups.md)