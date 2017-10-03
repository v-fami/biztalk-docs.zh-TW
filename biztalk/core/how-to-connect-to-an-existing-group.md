---
title: "如何連接到現有的群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.procedure.connecttogroup
helpviewer_keywords:
- groups, existing
- groups, connecting
- managing [groups], connecting
ms.assetid: 1eedbcd5-f3f1-4da5-b91c-67377131f889
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b452ef2f29eb5019eb126181e0cd47b66f82f7b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-connect-to-an-existing-group"></a>如何連接至現有的群組
您可以使用企業中任何電腦上的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，從遠端管理企業內一或多個 BizTalk Server 群組，只要這些群組位於相同網域或信任網域中的電腦上。  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] BizTalk Server 管理主控台中的 [系統管理] 節點是所有的 BizTalk 群組的最高層級節點以及層級使用時將現有的 BizTalk Server 群組加入 BizTalk Server 管理主控台。 在新增群組時，必須指定您要連接的現有伺服器與「BizTalk 管理」資料庫。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員登入，或以「BizTalk Server 系統管理員」群組的成員登入。  
  
### <a name="to-connect-to-an-existing-group"></a>連接至現有的群組  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，以滑鼠右鍵按一下**BizTalk Server 管理**，然後按一下 **連接至現有的群組**。  
  
3.  在**連接至現有的 BizTalk Server 組態資料庫**對話方塊中，於**SQL Server 名稱**下拉式清單方塊中，選取裝載 BizTalk 的 Microsoft SQL Server 執行個體的名稱管理資料庫 （也稱為 「 組態 」 資料庫）。 當您選取 SQL Server 執行個體時，BizTalk Server 會自動嘗試偵測位於該電腦上的 BizTalk Server 資料庫。  
  
4.  在**資料庫名稱**下拉式清單方塊中，選取 BizTalk Server 管理資料庫 (**BizTalkMgmtDb**) 至您要連接，，然後按一下**確定**。  
  
     BizTalk Server 管理主控台會將 BizTalk Server 群組加入至主控台樹狀目錄中。  
  
    > [!NOTE]
    >  如果 BizTalk Server 管理資料庫位於 SQL Server 叢集上，而叢集正在進行容錯移轉，那麼當您嘗試連接管理資料庫時，就可能收到類似下列的錯誤：  
    >   
    >  無法載入群組 [\<伺服器名稱 >:\<管理資料庫 >] 資料提供者。  
    >   
    >  And  
    >   
    >  其他資訊:  
    >   
    >  找不到 WMI 類別的執行個體。 (WinMgmt)  
    >   
    >  發生這個錯誤的原因，是因為在進行容錯移轉時，無法使用 BizTalk 資料庫。 若要解決這個問題，請等候 SQL Server 的叢集執行個體之後，才是線上然後再嘗試將它連接到 BizTalk Server 管理主控台。  
  
## <a name="see-also"></a>另請參閱  
 [管理群組](../core/managing-groups.md)   
 [BizTalk 群組](../core/biztalk-groups.md)