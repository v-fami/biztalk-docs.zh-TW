---
title: 如何修改群組屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying, groups
- configuring, groups
- groups, configuring
- managing [groups], properties
- groups, modifying
- managing [groups], modifying
- groups, properties
ms.assetid: 59e0853d-81b0-43f9-85bf-099868e25fad
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a191011b6824086e26c72ce5e5a182a167ca0e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254862"
---
# <a name="how-to-modify-group-properties"></a>如何修改群組屬性
您可以使用這個程序來設定 BizTalk Server 群組的全域屬性，以便選取簽章憑證、修改快取重新整理間隔，並决定 BizTalk Server 將如何處理大型訊息。 如需 BizTalk Server 群組屬性的詳細資訊，請參閱[BizTalk 群組](../core/biztalk-groups.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-biztalk-group-properties"></a>設定 BizTalk 群組屬性  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **屬性**。  
  
3.  在**群組內容**對話方塊**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入群組名稱。 群組名稱的長度不能超過 128 個字元。 此方塊中的名稱旁會顯示**群組**在主控台樹狀目錄中，以及伺服器名稱和 BizTalk 管理資料庫名稱的節點。|  
    |**Server**|顯示實際儲存「BizTalk 管理」資料庫的伺服器。|  
    |**資料庫**|顯示儲存此群組之所有組態設定的「BizTalk 管理」資料庫。|  
    |**SSO 伺服器名稱**|輸入這部電腦將用來儲存和存取配接器特定資訊的企業單一登入 (SSO) 伺服器名稱。 這是用來連接到 SSO 資料庫之 SSO 伺服器的名稱。|  
    |**BizTalk 系統管理員群組**|顯示系統管理員群組名稱，此群組在安裝完成後擁有管理 BizTalk Server 環境的權限。|  
    |**BizTalk 操作員群組**|顯示擁有檢視組態、執行查詢及執行電腦維護與基本應用程式監控之權限的操作員群組名稱。|  
    |**BizTalk Server B2B 操作員**|顯示 B2B 操作員群組的名稱。|  
  
4.  在**資料庫**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**資料庫**|顯示在設定期間所指定之應用程式中的所有資料庫名稱，以及資料庫所在的伺服器。|  
  
5.  在**憑證**索引標籤上，執行下列工作，，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**一般名稱**|顯示選取憑證的描述。|  
    |**憑證指紋**|顯示私密金鑰憑證的指紋，此私密金鑰憑證是用以數位簽章來自此群組的輸出訊息。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。|  
    |**移除憑證**|按一下以移除顯示的憑證。|  
    |**瀏覽**|按一下即可顯示**選取憑證**對話方塊中，選取您想要使用與群組目前的使用者或個人存放區簽章憑證的位置。|  
  
## <a name="see-also"></a>另請參閱  
 [管理群組](../core/managing-groups.md)   
 [BizTalk 群組](../core/biztalk-groups.md)   
 [如何將伺服器新增至群組](../core/how-to-add-a-server-to-a-group.md)   
 [如何將伺服器從一個群組移至另一個](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md)